
Crosscloud is a decentralized system, still being developed, which is
intended to give users the freedom to move comfortably between
competing cloud-based applications.  Where today users are locked in
by sites which hold onto their data and their social connections, when
crosscloud (or something like it) is widely deployed, users will be free 
to switch to new applications in search of better features, pricing, 
and policies.

The flagship Crosscloud application is [cimba](http://cimba.co), a
microblogging tool being built at MIT CSAIL.  Cimba users get an
experience like that provided by Twitter, Facebook news feeds, etc,
but they can switch to another Crosscloud microblogging app and still
see the same social network with the same posts and the same metadata.
More impressively, they can also switch vendors for their back-end
data storage with no impact on user experience for themselves or their
contacts.  (At least that's the vision; it's not there yet.)  Many
other Crosscloud applications are possible, spanning the whole range
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
      the system, and scaring away users and ecosystem participants).
      So the overall system is likely to be as reliable as the
      Internet in general.  Individual servers might be unreliable,
      but since users can easily switch, there should be strong market
      pressure toward reliability.

  - **Customizability.** Also known as "hackability" or "modability",
      the ability of a system to be tinkered with and modified to suit
      particular needs is important to adoption and user satisfaction.
      Centralized systems have a much harder time supporting this.

  - **Cost Savings.** Because the barriers to entry for competitors
      are much lower, prices are likely to be lower.

## Challenge

To make the crosscloud vision a reality, three main things have to happen:

### 1.  Research

There are some open questions in computer science about whether it's
feasible to build a decentralized system of this scale, with these
characteristics.

So we need to build demonstration apps (eg cimba) and publishing any
new science we do in the process.  This is: prove that it can be built
by building it.

### 2.  Standards

Building a system with the right properties is not enough.  It has to be something that is easy enough to implement that it ends up widely deployed, as the only system like this.   Imagine if instead of the Internet, we had several different global networks, and you could only reach the people on the same one.   (Some of us remember those days, with BITNET, uucp, etc.)

This means people working toward the crosscloud vision need to work together to reach consensus on the protocols.  And during the time before consensus is reached, people will need to keep updating their software.   At some point along the way, Crosscloud may need to merge with similar systems for the benefit of the users.

At this point, the [Linked
Data](http://en.wikipedia.org/wiki/Linked_data) technology stack is
being used and extended to build crosscloud systems, with standards
work being done at W3C.  We view the crosscloud vision as one of the driving
use cases for Linked Data.  

### 3.  Ecosystem

Even if the technology works well and there is complete consensus on
the standards, if there aren't enough applications or service providers, users wont have the intended level of freedom and benefits.

So it's important to make sure there are plenty of people able and willing to build crosscloud applications and run crosscloud servers.

## Projects

Crosscloud development is led by Sandro Hawke and Tim Berners-Lee at
MIT and involves various projects around the world.  Related projects
that are not part of the Crosscloud effort, but might converge
eventually, are being listed on the [reading list](reading-list.md).

- [cimba](http://cimba.co) is a microblogging client ([source code](https://github.com/linkeddata/cimba/))

- ldphp is an LDP server, providing some of the crosscloud server functionality ([source code](https://github.com/linkeddata/ldphp))

- librdf.js is a JavaScript library for webapp developers to access needed functionality ([source code](https://github.com/linkeddata/rdflib.js))





  


