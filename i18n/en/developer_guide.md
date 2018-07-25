# Guidelines
- We aim for complete C++11/14 compliance; please use this to your advantage
- Please use the standard library and dependency libraries whenever possible

## Vulnerability Response
- Our [Vulnerability Response Process](https://github.com/monero-project/meta/blob/master/VULNERABILITY_RESPONSE_PROCESS.md) encourages responsible disclosure
- We are also available via [HackerOne](https://hackerone.com/monero)

## Style
1. Read [Google's C++ Style Guide](https://google.github.io/styleguide/cppguide.html) (particularly for non-formatting style reference)
   - If bash programming, read [Google's Shell Style Guide](https://github.com/google/styleguide/blob/gh-pages/shell.xml)
2. For files containing only new work, run [clang-format](http://clang.llvm.org/docs/ClangFormat.html) with ```-style=file``` (which uses our provided [.clang-format](https://github.com/monero-project/kovri/blob/master/.clang-format))
```bash
$ cd kovri/ && clang-format -i -style=file src/path/to/my/file
```
3. For files with mixed (existing + new) work, run [clang-format](http://clang.llvm.org/docs/ClangFormat.html) selectively over only lines directly related to the new work.
   - See [vim](http://clang.llvm.org/docs/ClangFormat.html#vim-integration) and [emacs](http://clang.llvm.org/docs/ClangFormat.html#emacs-integration) documentation for examples of configuring keybindings for `clang-format` plugins.
4. Run [cpplint](https://github.com/google/styleguide/tree/gh-pages/cpplint) (which uses our provided [CPPLINT.cfg](https://github.com/monero-project/kovri/blob/master/CPPLINT.cfg)) to catch any issues that were missed by clang-format
```bash
$ cd kovri/ && cpplint src/path/to/my/file && [edit file manually to apply fixes]
```

### Plugins

- Vim integration
  - [clang-format](http://clang.llvm.org/docs/ClangFormat.html#vim-integration)
  - [clang-format ubuntu 16.04 vim workaround](http://stackoverflow.com/questions/39490082/clang-format-not-working-under-gvim)
  - [cpplint.vim](https://github.com/vim-syntastic/syntastic/blob/master/syntax_checkers/cpp/cpplint.vim)
- Emacs integration
  - [clang-format](http://clang.llvm.org/docs/ClangFormat.html#emacs-integration) + [clang-format.el](https://llvm.org/svn/llvm-project/cfe/trunk/tools/clang-format/clang-format.el)
  - [flycheck-google-cpplint.el](https://github.com/flycheck/flycheck-google-cpplint)

### Amendments to Google's proposed C++ style

- Avoid prepended mixed-case ```k``` and MACRO_TYPE for all constants
- Use Doxygen three-slash ```/// C++ comments``` when documenting for Doxygen
- Try to document all your work for Doxygen as you progress
- If anonymity is a concern, try to blend in with a present contributor's style

### Optional Checks
1. [cppdep](https://github.com/rakhimov/cppdep)
   for component dependency, physical insulation, and include checks.
2. [cppcheck](https://github.com/danmar/cppcheck/) for static analysis
   (complementary to Coverity).
3. [lizard](https://github.com/terryyin/lizard) for code complexity checks.

## Sending your work
To contribute your work, please proceed with the following:

1. [Fork](https://help.github.com/articles/fork-a-repo/) Kovri
2. Review the style section of this document
3. Create a [topic branch](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)
   - We currently do not have any tags as we are in Alpha. For now, you can base your work off of master
4. Make changes
   - Commits should be [atomic](https://en.wikipedia.org/wiki/Atomic_commit#Atomic_commit_convention) when possible and diffs should be easy to read
   - Please try to not mix formatting fixes with non-formatting commits
5. Be courteous of the git-log
   - Commit title should prepend class or aspect of project. For example, "HTTPProxy: implement User-Agent scrubber. Fixes #193." or "Garlic: fix uninitialized padding in ElGamalBlock"
   - Commit messages should be verbose by default, consisting of a short subject line (50 chars max), a blank line, and detailed explanatory text as separate paragraph(s) - unless the title alone is self-explanatory
   - If a particular commit references another issue, please add a reference. For example; *See #123*, or *Fixes #123*. This will help us resolve issues when we merge into `master`
   - If a particular commit is rebased after collaboration within a pull-request, please reference the pull-request number within the commit message. For example; *References #123*
6. [**Sign**](https://git-scm.com/book/en/v2/Git-Tools-Signing-Your-Work) your commit(s) and, if you are a new contributor, open a new pull-request which adds your PGP key to our repository (see contrib)
7. Send a pull-request to branch `master`
   - The body of the pull request should contain an accurate description of what the patch does and should also provide justification/reasoning for the patch (when appropriate). You should include references to any discussions such as other issues or chats on IRC

## Proposals
To contribute a proposal, please review our [open issues](https://github.com/monero-project/kovri/issues) for existing proposals. If what you propose is not there, then [open a new issue](https://github.com/monero-project/kovri/issues/new).

Even though our C4 dictates that we merge everything, we ask that you open a proposal for the following reasons:

1. A proposal opens up communication
2. A proposal shows that the contributor respects the input of all project collaborators
3. A proposal allows seamless collaborator input in an open forum
4. A proposal saves time if a collaborator is working on a similar feature/issue
5. A proposal prevents catastrophes and mishaps or allows collaborators to prepare for catastrophes and mishaps

*Not* opening a proposal will *not* prevent you from contributing; we will merge what you PR - but a proposal is highly recommended.

## TODO's
- Do a quick search in the codebase for ```TODO(unassigned):``` and/or pick an issue and start patching!
- If you create a TODO, assign it to yourself or write in ```TODO(unassigned):```

## Fuzz testing

From [reference](http://llvm.org/docs/LibFuzzer.html) : "LibFuzzer is under active development so you will need the current (or at least a very recent) version of the Clang compiler"

Get a recent version of clang:

```bash
$ cd ~/ && mkdir TMP_CLANG && git clone https://chromium.googlesource.com/chromium/src/tools/clang TMP_CLANG/clang
$ ./TMP_CLANG/clang/scripts/update.py
$ cd --
```

Get libFuzzer:

```bash
$ git clone https://chromium.googlesource.com/chromium/llvm-project/llvm/lib/Fuzzer contrib/Fuzzer
```

Build kovri with fuzz testing enabled:

```bash
$ PATH="~/third_party/llvm-build/Release+Asserts/bin:$PATH" CC=clang CXX=clang++ make fuzz-tests
```

Usage (Example for RouterInfo):

```bash
mkdir RI_CORPUS MIN_RI_CORPUS
find ~/.kovri/core/network_database/ -name "router_info*" -exec cp {} RI_CORPUS \;
./build/kovri-util fuzz --target=routerinfo -merge=1 MIN_RI_CORPUS RI_CORPUS
./build/kovri-util fuzz --target=routerinfo -jobs=2 -workers=2 MIN_RI_CORPUS
```

# Quality Assurance

The following is a proposed model for QA workflow. While linear in nature, any phase can be worked on individually if needed - as long as all phases are eventually addressed.

## Phase 1: Basic Review

- Review open issues on our [Issue Tracker](https://github.com/monero-project/kovri/issues/)
- Review our [Vulnerability Response Process](https://github.com/monero-project/meta/blob/master/VULNERABILITY_RESPONSE_PROCESS.md)
- All code must adhere to our contributing guidelines
- Note areas that need improving (mentally or in code)
- Create TODO's and assign if possible

## Phase 2: Specification Review /  Implementation / Code Documentation

- Complete specification review on a per module basis; e.g., Streaming, I2PControl, etc.
  - Code must be in-line with essential parts of the specification that will maintain the same (or better) level of anonymity that java I2P provides
  - Refactor/implement/patch when/where needed
- Ensure C++11/14 compliant implementation
  - Review phase 2 if needed
- Resolve all related TODO's
- Document code as much as possible with inline comments and Doxygen
  - Code should be understood by novice to experienced coders
  - Code should guide the reader to a better understanding of I2P
    - I2P is very complex so our code should act as sovereign replacement of spec documentation and not simply as a supplement (this can be a tedious objective but very rewarding in terms of maintenance and software lifespan)

## Phase 3: Crypto Review / Security auditing

- Ensure that crypto is up-to-date and properly implemented
- Establish every vector for known exploitation
  - Keep these vectors in mind when writing tests
- Break Kovri every which-way possible
  - Fix what you break
- Always use trustworthy, well-written libraries when possible
  - Avoid homebrewed, ad-hoc, *I'm sure I know better than the community* type of code
- Seek a 2nd (or more) opinion(s) from colleagues before proceeding to next phase

## Phase 4: Bug squashing / Tests / Profiling

- Resolve priority bugs/issues
- Write unit-tests tests for every module
  - Run tests. Run them again
  - Full review of test results. Patch if needed. Refactor as necessary
- Ensure that automation is running on a regular basis
  - valgrind, doxygen, clang-format
  - Patch if needed, refactor as necessary

## Phase 5: Confer

- Confer with colleagues and the community
  - Conferring should be done publicly via issues, meetings, and/or IRC
- Accept all feedback and, in response, produce tangible results
- If satisfied, proceed with next phase, else repeat this phase (or start from a previous phase)

## Phase 6: Repeat the cycle from the beginning

# [Code of Conduct (22/C4.1)](http://rfc.zeromq.org/spec:22)

## License

Copyright (c) 2009-2015 Pieter Hintjens.

This Specification is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation; either version 3 of the License, or (at your option) any later version.

This Specification is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program; if not, see <http://www.gnu.org/licenses>.

## Language

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in RFC 2119.

## Goals

C4 is meant to provide a reusable optimal collaboration model for open source software projects. It has these specific goals:

- To maximize the scale and diversity of the community around a project, by reducing the friction for new Contributors and creating a scaled participation model with strong positive feedbacks;
- To relieve dependencies on key individuals by separating different skill sets so that there is a larger pool of competence in any required domain;
- To allow the project to develop faster and more accurately, by increasing the diversity of the decision making process;
- To support the natural life cycle of project versions from experimental through to stable, by allowing safe experimentation, rapid failure, and isolation of stable code;
- To reduce the internal complexity of project repositories, thus making it easier for Contributors to participate and reducing the scope for error;
- To enforce collective ownership of the project, which increases economic incentive to Contributors and reduces the risk of hijack by hostile entities.

## Design

### Preliminaries

- The project SHALL use the git distributed revision control system.
- The project SHALL be hosted on github.com or equivalent, herein called the "Platform".
- The project SHALL use the Platform issue tracker.
- The project SHOULD have clearly documented guidelines for code style.
- A "Contributor" is a person who wishes to provide a patch, being a set of commits that solve some clearly identified problem.
- A "Maintainer" is a person who merges patches to the project. Maintainers are not developers; their job is to enforce process.
- Contributors SHALL NOT have commit access to the repository unless they are also Maintainers.
- Maintainers SHALL have commit access to the repository.
- Everyone, without distinction or discrimination, SHALL have an equal right to become a Contributor under the terms of this contract.

### Licensing and Ownership

- The project SHALL use a share-alike license, such as the GPLv3 or a variant thereof (LGPL, AGPL), or the MPLv2.
- All contributions to the project source code ("patches") SHALL use the same license as the project.
- All patches are owned by their authors. There SHALL NOT be any copyright assignment process.
- The copyrights in the project SHALL be owned collectively by all its Contributors.
- Each Contributor SHALL be responsible for identifying themselves in the project Contributor list.

### Patch Requirements

- Maintainers and Contributors MUST have a Platform account and SHOULD use their real names or a well-known alias.
- A patch SHOULD be a minimal and accurate answer to exactly one identified and agreed problem.
- A patch MUST adhere to the code style guidelines of the project if these are defined.
- A patch MUST adhere to the "Evolution of Public Contracts" guidelines defined below.
- A patch SHALL NOT include non-trivial code from other projects unless the Contributor is the original author of that code.
- A patch MUST compile cleanly and pass project self-tests on at least the principle target platform.
- A patch commit message SHOULD consist of a single short (less than 50 character) line summarizing the change, optionally followed by a blank line and then a more thorough description.
- A "Correct Patch" is one that satisfies the above requirements.

### Development Process

- Change on the project SHALL be governed by the pattern of accurately identifying problems and applying minimal, accurate solutions to these problems.
- To request changes, a user SHOULD log an issue on the project Platform issue tracker.
- The user or Contributor SHOULD write the issue by describing the problem they face or observe.
- The user or Contributor SHOULD seek consensus on the accuracy of their observation, and the value of solving the problem.
- Users SHALL NOT log feature requests, ideas, suggestions, or any solutions to problems that are not explicitly documented and provable.
- Thus, the release history of the project SHALL be a list of meaningful issues logged and solved.
- To work on an issue, a Contributor SHALL fork the project repository and then work on their forked repository.
- To submit a patch, a Contributor SHALL create a Platform pull request back to the project.
- A Contributor SHALL NOT commit changes directly to the project.
- If the Platform implements pull requests as issues, a Contributor MAY directly send a pull request without logging a separate issue.
- To discuss a patch, people MAY comment on the Platform pull request, on the commit, or elsewhere.
- To accept or reject a patch, a Maintainer SHALL use the Platform interface.
- Maintainers SHOULD NOT merge their own patches except in exceptional cases, such as non-responsiveness from other Maintainers for an extended period (more than 1-2 days).
- Maintainers SHALL NOT make value judgments on correct patches.
- Maintainers SHALL merge correct patches from other Contributors rapidly.
- The Contributor MAY tag an issue as "Ready" after making a pull request for the issue.
- The user who created an issue SHOULD close the issue after checking the patch is successful.
- Maintainers SHOULD ask for improvements to incorrect patches and SHOULD reject incorrect patches if the Contributor does not respond constructively.
- Any Contributor who has value judgments on a correct patch SHOULD express these via their own patches.
- Maintainers MAY commit changes to non-source documentation directly to the project.

### Creating Stable Releases

- The project SHALL have one branch ("master") that always holds the latest in-progress version and SHOULD always build.
- The project SHALL NOT use topic branches for any reason. Personal forks MAY use topic branches.
- To make a stable release someone SHALL fork the repository by copying it and thus become maintainer of this repository.
- Forking a project for stabilization MAY be done unilaterally and without agreement of project maintainers.
- A stabilization project SHOULD be maintained by the same process as the main project.
- A patch to a stabilization project declared "stable" SHALL be accompanied by a reproducible test case.

### Evolution of Public Contracts

- All Public Contracts (APIs or protocols) SHALL be documented.
- All Public Contracts SHOULD have space for extensibility and experimentation.
- A patch that modifies a stable Public Contract SHOULD not break existing applications unless there is overriding consensus on the value of doing this.
- A patch that introduces new features to a Public Contract SHOULD do so using new names.
- Old names SHOULD be deprecated in a systematic fashion by marking new names as "experimental" until they are stable, then marking the old names as "deprecated".
- When sufficient time has passed, old deprecated names SHOULD be marked "legacy" and eventually removed.
- Old names SHALL NOT be reused by new features.
- When old names are removed, their implementations MUST provoke an exception (assertion) if used by applications.

### Project Administration

- The project founders SHALL act as Administrators to manage the set of project Maintainers.
- The Administrators SHALL ensure their own succession over time by promoting the most effective Maintainers.
- A new Contributor who makes a correct patch SHALL be invited to become a Maintainer.
- Administrators MAY remove Maintainers who are inactive for an extended period of time, or who repeatedly fail to apply this process accurately.
- Administrators SHOULD block or ban "bad actors" who cause stress and pain to others in the project. This should be done after public discussion, with a chance for all parties to speak. A bad actor is someone who repeatedly ignores the rules and culture of the project, who is needlessly argumentative or hostile, or who is offensive, and who is unable to self-correct their behavior when asked to do so by others.

# Governance Process

![Governance Process](https://getmonero.org/blog/assets/2015-year-in-review/governance-process.jpg)
