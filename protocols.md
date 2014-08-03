
# Crosscloud Protocols

This document lists protocols (including protocol elements such as formats and vocabularies) under consideration.  They range for existing standards to blue sky ideas for possible future protocols.

## Identity

### WebID TLS (~10 impls)

### Account Creation (1 impl)

### Account Provider Self-Description
  
### WebID TLS delegation (1 impl)

### Nonce Loop Authentication (0 impls)

### foaf userinfo at WebID (~100 impls)


## Data Access

### LDP Basic Containers (~10 impls)

### LDP Paging

### LDPNext

Various, see https://www.w3.org/2012/ldp/wiki/LDPNext

### Link-Following SPARQL (1-5 impl)

ISSUE: SeeAlso

ISSUE: Writes

ISSUE: Syntactic Flag, WHEREVER

### Controlling Access Control

as seen in ld-php

### Resource Metadata

as seen in ld-php / Warp


## Data Dynamics

### WebMention

### SiteWatch

### C-SPARQL

### needed: volunteer proxies



## Apps

### app metadata for directory (not spec'd)



## Vocabulary Management

### mics MicroSpec Vocabulary (0 impls)

For floating linked data

http://w3.org/ns/mics

### Webtree (0 impls)

expressing mirroring & moving of web space

### trigr (trig with rules) (not specd)

"RULE x:a { foo }" as syntactic sugar for spin?

### SPARQL JavaScript External Function Interface (sparql-jsefi)

Something like:

   function isOdd(req) {
      return req.arg(1).asNumber() % 2 == 1
   }



