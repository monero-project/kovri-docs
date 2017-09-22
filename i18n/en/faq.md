# Frequently Asked Questions

## Table of Contents
- General Questions
  - What is Kovri?
  - Who is developing Kovri?
  - How will Kovri help Monero?
  - Why should I get Kovri instead of I2P?
  - What does Kovri do/not do for you?
  - What is the current state of Kovri?
  - When is the alpha
  - What is the development team currently focusing on?
  - What is the current usability of Kovri and the privacy it offers?
  - How can I get a hold of the Kovri developers?
- Kovri vs i2pd
  - Why should I use Kovri instead of i2pd?
  - What are the biggest differences between Kovri and i2pd?
  - Why did you fork from i2pd?
  - What were the turning points that lead to forking from i2pd (and why are there two i2pd repositories: one on Bitbucket and one on GitHub)?
- Using Kovri
  - I found a vulnerability! I found a bug! What do I do?
  - Why does my log show a date/time different from my timezone?

## General Questions

### What is Kovri?

[Kovri](https://getmonero.org/resources/moneropedia/kovri.html) is a free, decentralized, anonymity technology developed by [Monero](https://getmonero.org).

Currently based on [I2P](https://getmonero.org/resources/moneropedia/i2p.html)'s open specifications, Kovri uses both [garlic encryption](https://getmonero.org/resources/moneropedia/garlic-encryption.html) and [garlic routing](https://getmonero.org/resources/moneropedia/garlic-routing.html) to create a private, protected overlay-network across the internet. This overlay-network provides users with the ability to *effectively* hide their geographical location and internet IP address.

Essentially, Kovri *covers* an application's internet traffic to make it anonymous within the network.

A lightweight and security-focused router, Kovri is fully compatible with the I2P network. An alpha version of Kovri is in the works.

### Who is developing Kovri?
Kovri is an open-source project, which means that it depends on the community for contributions. The lead developer on the project is [anonimal](https://github.com/anonimal), who you can reach with questions on the Kovri IRC channels [#kovri](irc://chat.freenode.net/#kovri), [#kovri-dev](irc://chat.freenode.net/#kovri), and his [Twitter account](https://twitter.com/0x914409F1).

Kovri is being developed under the umbrella of [The Monero Project](https://github.com/monero-project), which is another open-source project that develops the [Monero coin](https://getmonero.org) and [Open Alias](https://openalias.org). The relationship between The Monero Project and Kovri is a mutually beneficial one, with Kovri looking to integrate into the Monero network, and Monero providing a stream of developers and resources for Kovri development.

### How will Kovri help Monero?
Monero is a secure, private, untraceable, and fungible cryptocurrency that has privacy on by default, and utilizes such technologies as stealth addresses, RingCT, and ring signatures to hide the receiver, amounts, and sender respectively. Some potential weaknesses in Monero are leaking the IP address that broadcasts a transaction and correlation attacks.

Enter Kovri. Kovri will be implemented into the official Monero wallet, so all transactions will be routed through the Kovri anonymous network, hiding the IP address from which the transaction originated. In the future, all transactions will be routed through Kovri by default, although downloading the blockchain will still be through the clearnet for efficiency.

### Why should I get Kovri instead of I2P?
[I2P](https://geti2p.net) is a great project, but there were a few things that we felt needed tweaking to integrate the technology into Monero. First, I2P is developed in Java, and we thought that developing a router in C++ would help the code be fast and lightweight.

Secondly, while the Java implementation of I2P is great, it comes with a lot of extra features that we don't feel are necessary for the Monero application to use. So, we decided to start from scratch, and make a router that is JUST the router. This bare-bones approach is perfect for Monero, and is also good news for others that want to make I2P applications. They have the option to use a lightweight router without all the excess bloat, while other users who have a use for those extra features will be able to use the Java implementation. It's a win-win for everybody.

### What does Kovri do now?
- Allows you to become a node on the I2P network
- Hides your physical location from the sites you visit
- Anonymizes you on IRC and allows anonymous Email
- Allows you to host anonymous websites or services
- Provides funding to developers, hackers, researchers via the FFS and HackerOne
- Aims for rigorous code-quality and dev standards

### What developments does Kovri have in store for the future?
- Commits Monero transactions over I2P
- GUI for improved configuration and usability
- Library API and bindings for external apps/libs
- Firefox extension to easily access eepsites
- Website Development (getkovri.org / kovri.i2p)
- Extensive documentation from ELI5 to developer

### What will Kovri not do for you?
- Sacrifice your security for ulterior motives
- Provide a convoluted, painful web user interface
- Require authorities for network consensus
- Access to internet websites via an "outproxy"
- Require a performance-killing Java VM
- Walk your dog or favorite pet, pay your taxes

### What is the current state of Kovri?
Kovri is in active development and currently is in a pre-alpha phase. It's *not* yet integrated with Monero, but, in addition to several core features, we are developing a [client](https://github.com/monero-project/kovri/issues/351) and [core](https://github.com/monero-project/kovri/issues/350) API for monero, and other applications, to use.

But just because we're in pre-alpha doesn't mean you can't use Kovri. Currently, you can use Kovri to connect to (and partake in) the I2P network, browse eepsites, connect to IRC, and run client and server tunnels.

### When is the alpha?
An alpha release is in the works to be released (we hope!!) before the end of 2017. Once we're in alpha, work immediately begins on the beta release, which will require: a fully implemented API, resolution to essential quality assurance issues, and various bug fixes.

### What is the development team currently focusing on?
Currently, we are focusing on everything listed in our [issues tracker](https://github.com/monero-project/kovri/issues/). They cover a bulk of what we need to finish before the official alpha release.

### What is the current usability of Kovri and the level of privacy it offers?
Kovri is usable to the extent of what `./kovri --help` has to offer. Kovri currently has no interaction with Monero. With regard to privacy, we have fixed many security issues since inception, but we ask you to keep in mind that we are still in pre-alpha.

There is still much code to cover, so don't expect a strong guarantee of anonymity like with Tor, or even Java I2P. Those projects have 10+ years of research and implementation experience, and we're just getting started.

Feel free to play the role of developer and experiment with Kovri, but only if **not** being anonymous doesn't put you in danger, as there is always the risk of possible de-anonymization due to being in pre-alpha (this is not unique to Kovri).

### How can I get a hold of the Kovri developers?
See our [README](https://github.com/monero-project/kovri/blob/master/README.md).

## Kovri vs i2pd

### Why should I use Kovri instead of i2pd?

- Security: our focus is on securing our software; not [rushing to get things done](https://github.com/monero-project/kovri/issues/65) for the sake of having a release
- Quality: you're supporting efforts to ensure a quality codebase that will stand the test of time. This includes all aspects of code maintainability
- Monero: you will be supporting a crypto-currency that prides itself on privacy-preservation and anonymity while increasing both your privacy and anonymity

### What are the biggest differences between Kovri and i2pd?

- We provide a [Forum Funding System](https://forum.getmonero.org/8/funding-required) for features/development.
- We focus on creating a ["secure by default"](http://www.openbsd.org/security.html), easily maintainable, more-likely-to-be-reviewed I2P router. This will come with the cost of dropping lesser-used features found in the other routers, but core functionality and an API will be fully intact. By creating a smaller, efficient, "bare-bones" router, we will provide developers and researchers more time for security auditing and more time to question the I2P design and specifications.
- We focus on implementing an intuitive, developer-friendly API for any application to connect to and use the I2P network; this includes Monero.
- We provide both end-users and developers a [quality assurance](https://github.com/monero-project/kovri/issues/58) and [development model](https://github.com/monero-project/kovri-docs/blob/master/i18n/en/contributing.md) in order to provide better software for everyone.
- We will implement alternative reseeding options so users can use [Pluggable Transports](https://www.torproject.org/docs/pluggable-transports.html.en) instead of HTTPS for reseed.
- We will implement extended functionality *(hidden mode + disabled inbound)* to provide anonymity for those who live in countries with extreme conditions or those firewalled by carrier-grade NAT or DS-Lite.
- We will always create a welcome environment for collaboration.
- We will always listen to your feedback and do our best to improve Kovri!

### Why did you fork from i2pd?

We forked for at least several reasons:

- We wanted a robust, secure, and viable C++ implementation of the I2P network; and i2pd was not delivering
- We wanted a positive community that encouraged collaboration for the betterment of the software; not negative, narcissist glory
- We wanted a lead developer who could lead; not someone who could ignore requests for responsible disclosure or tuck-tail-and-run when faced with collaborator conflict

### What were the turning points that lead to forking from i2pd (and why are there two i2pd repositories: one on Bitbucket and one on GitHub)?

*So began the drama of i2pd*.

In early/mid 2015, one of the developers with push privileges on GitHub pushed a commit(s) that i2pd's first author did not like. Instead of working together to resolve the issue, said author took i2pd to Bitbucket, deleted **all** existing git history, and made himself sole 'contributor' of the software. He then vowed to never return to Irc2P.

These actions offended many in the I2P community, including the developers, and nearly ended the C++ project.

In the fall of 2015, along came anonimal who, not wanting to see everyone's work to go to waste, revived the project through contributions of their own and by reigning-in development. An open invitation for all remaining active developers to meet and discuss i2pd's future was then given. i2pd's first author never showed but the act of meeting apparently rustled i2pd's feathers to the point where he [retaliated](https://github.com/PurpleI2P/i2pd/issues/279) and began to work on GitHub again - but this time within an ```openssl``` branch (which turned out to be the Bitbucket repository) instead of the community-driven ```master``` branch.

Seeing that this sort of erratic behavior would only hurt the I2P network and the project as a whole, the remaining developers continued to have [several important meetings](https://github.com/monero-project/kovri/issues/47) and set the foundation for what is now Kovri.

## Using Kovri

### I found a vulnerability! I found a bug! What do I do?
- Vulnerabilities: see our [README](https://github.com/monero-project/kovri/blob/master/README.md)
- Bugs: see our [Contributing Guide](https://github.com/monero-project/kovri-docs/blob/master/i18n/en/contributing.md)

### Why does my log show a date/time different from my timezone?
Logs are recorded in UTC to protect your privacy. By using UTC, you are in a better position to upload log pastes to share with developers or the community without impacting your anonymity.
