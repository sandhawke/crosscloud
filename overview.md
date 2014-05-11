
## Vision

The **crosscloud vision** is of people easily moving between
applications, always able to access and control their own data.  The
name comes from the observation that cloud-based software has a strong
tendency to lock-in users, so we need a good way to cross between
these different "clouds".  This vision goes beyond what is provided
today by cloud data storage services like owncloud and dropbox, in
that it requires applications to use interoperable data formats and
support integrated social data sharing.  The goal is here is that when
users select different products, they never lose access to what
they've been doing and the people they've been doing it with.

The flagship crosscloud application is cimba, a microblogging tool
similar to Twitter and others, but decentralized.  Cimba users can
switch to another crosscloud microblogging app and still see the same
social network with the same posts and the same metadata.  More
impressively, they can also switch vendors for their back-end data
storage with no impact on user experience for themselves or their
contacts.

Many other crosscloud applications are possible, spanning the whole
range of Web 2.0 success stories.   For some details see @@apps..

## Benefits

While consumers having a freedom of choice in the market may seem like
a goal it itself, its value comes from what else it will enable.  Some
of the benefits of using crosscloud software:

  - **Innovation.** When your data and social connections are locked
      in to one platform or application, it's hard to try out
      interesting alternatives.  Even if you try them, it's hard to
      make the switch, because all your history and previous work is
      in your old system.  Your social connections are on the old
      system, too.  Can you get all your friends or colleagues to
      move at the same time?  And if people like you don't switch, new
      systems will fail for lack of users.  When users are locked in,
      innovaation is locked out.

  - **Connection.** For a variety of reasons, certain people you know
      probably can't or won't use any particular social networking
      platform.  This makes it hard to difficult to connect with them
      online, whether it's for real work or just for fun.  With a
      large enough group of people (sometimes only 5 or 10) it's
      impossible to find a platform they all use.  In contrast, With
      crossclouds software, people will have a wide variety of vendors and
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
      coerce users to grant intimate access to their data.  Crosscould
      systems don't prevent such access, but they do give users
      freedom to choose alternatives.

  - **Reliability.** The overall system will have no single point of
      failure (beyond IP connectivity and maybe the DNS).  If any
      subsystem is repeatedly unreliable, users can easily switch
      providers.

  - **Freedom of Choice.** If you don't like an application or data
      service provider, you can easily go elsewhere.  If there's
      no one in the market providing what you want, you can built it
      yourself (or hire someone to build it).

  - **Appropriate Controls.** The system is flexible about where
      control resides.  In consumer apps, it can stay with the user.
      But with enterprise apps, it's feasible to have control remain
      with the enterprise.

  - **Cost Savings.** because the barriers to entry for competitors
      are much lower, prices are likely to be lower.

## Challenge

To make the crosscloud vision a reality, three main things have to happen:

### 1.  Research

There are some open questions in computer science about whether it's
feasible to build a decentralized system of this scale, with these
characteristics.

So building cimba, podserver, demo apps; publishing any new science.
Prove that it can be built by building it.

We encourage others to help, showing that it can be built.

### 2.  Standards

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

If we build a single, unified system with all the right scaling properties, if customers can't find the products they want, we wont be done.

This is going to require businesses seeing how they can make money offering crosscloud products and services.

## Projects

- [cimba](http://cimba.co) is ...  [source code](https://github.com/linkeddata/cimba/)

- ld.php

- librdf

- [indx](https://github.com/sociam/indx/)

  


