
## Vision

The **crosscloud vision** is of people easily moving between
applications, always able to access and control their own data, never
forced to use products or services from any particular vendor.  The
name comes from the observation that cloud-based software has a strong
tendency to lock-in users and make them to use a particular platform.
In response, we need a good way to cross between these different cloud
systems.  The goal is that users everywhere be free to use different
products, and if they switch, they never lose access to what they've
been doing and the people they've been doing it with.

The flagship crosscloud application is [cimba](http://cimba.co), a
microblogging tool being built at MIT CSAIL.  Cimba users get an
experience like that provided by Twitter, Facebook news feeds, etc,
but they can switch to another crosscloud microblogging app and still
see the same social network with the same posts and the same metadata.
More impressively, they can also switch vendors for their back-end
data storage with no impact on user experience for themselves or their
contacts.  (At least that's the vision; it's not there yet.)  Many
other crosscloud applications are possible, spanning the whole range
of Internet success stories and dreams of a connected world (see
[potential application areas](apps.md)).

## Benefits

Freedom of choice in the market may seems like a goal in itself,
but its real value becomes clear when we consider the benefits that
will come with that freedom:

  - **Innovation.** When your data and social connections are locked
      in to one platform or application, it's hard to try out
      interesting alternatives.  Even if you try them, it's hard to
      make the switch, because all your history and previous work is
      in your old system.  Your social connections are on the old
      system, too.  Can you get all your friends or colleagues to
      move at the same time?  And if people like you don't switch, new
      systems will fail for lack of users.  When users are locked in,
      most serious innovation is locked out.

  - **Connection.** For a variety of reasons, certain people you know
      probably can't or won't use any particular social networking
      platform.  This makes it hard to connect with them
      online, whether it's for work or just for fun.  With a
      large enough group of people (sometimes only 5 or 10) it's
      impossible to find a platform they all use.  In contrast, With
      crosscloud software, people will have a wide variety of vendors and
      platforms to choose from.  As long as each person can find one
      that works for them, you can all be connected.

  - **Stability.** You can keep using the same version of the software
      as long as someone is willing to support it.  No more being
      forced to accept every product change or give up the product.

  - **Security.** Because crosscloud products never lock you are in,
      you are free to seek out providers who offer high levels of data
      security.  Because everyone is free to do this, we expect in
      time the market will provide many strong options.

  - **Privacy.** Although some invasions of privacy are due to
      failures in data security, many are part of routine business on
      the Internet today.  Advertising supported products, in general,
      coerce users to grant intimate access to their data.  Crosscloud
      systems don't prevent such access, but they do give users
      freedom to choose alternatives.

  - **Reliability.** A system providing crosscloud functionality
      has to be engineered without introducing any single point of
      failure (since control over that point would mean control over
      the system, and scaring away users and ecosystem participatens).
      So the overall system is likely to be as reliable as the
      Internet in general.  Individual servers might be unreliable,
      but since users can easily switch, there should be strong market
      pressure toward reliability.

  - **Customizability.** Also known as "hackability" or "modability",
      then ability of a system to be tinkered with and modified to
      suit particular needs is important to adoption and user
      satisfaction.  Centralized systems generally lack this, because
      @@@ ... what about distributing mods?

  - **Cost Savings.** Because the barriers to entry for competitors
      are much lower, prices are likely to be lower.

## Challenge

To make the crosscloud vision a reality, three main things have to happen:

### 1.  Research

@@

There are some open questions in computer science about whether it's
feasible to build a decentralized system of this scale, with these
characteristics.

So building cimba, podserver, demo apps; publishing any new science.
Prove that it can be built by building it.

We encourage others to help, showing that it can be built.

### 2.  Standards

@@

If we know how to build a system like crosscloud, and we build three different ones that don't interoperate, we're not in good shape.

So it's important the people defining the protocols make a reasonable effort to come to consensus on those protocols before they become so widely deployed they are hard to update.

As such, we suggest a system cannot consider itself a "crosscloud" system unless it conforms to all relevant W3C recommendations and its makers are engaged and committed to conforming to new relevant standards.

--


Building Crosscloud is an open standards effort, as various people
work on the technical challenges and gradually standardize elements
that become well understood.  While some implementations will be open
source, proprietary implementations are also welcome.  To be a part of
the Crosscloud ecosystem, software must conform to all applicable
specifications.  For now, while those specs are being debated and
refined, participating in Crosscloud requires being actively engaged
with the other Crosscloud developers and being willing to update your
software as needed.

The [Linked Data](http://en.wikipedia.org/wiki/Linked_data) technology
stack is being used and extended to build Crosscloud, with standards
work being done at W3C.  Where Linked Data is technology-driven, with
a wide range of use cases, Crosscloud is customer-driven, focussed on
the single use case of allowing people the freedom to easily move
between vendors, even in a cloud software world.  The two visions may
result in some of the same specifications, but there may be many other
uses for Linked Data, and it's not out of the question for Crosscloud
functionality to be provided with non-Linked Data technologies.

### 3.  Ecosystem

@@

If we build a single, unified system with all the right scaling properties, if customers can't find the products they want, we wont be done.

This is going to require businesses seeing how they can make money offering crosscloud products and services.

## Projects

- [cimba](http://cimba.co) is ...  [source code](https://github.com/linkeddata/cimba/)

- ld.php

- librdf

- [indx](https://github.com/sociam/indx/)

  


