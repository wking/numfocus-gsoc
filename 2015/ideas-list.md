# Table of Contents

Organizations are in alphabetic order.

- [Julia](#julia)
- [Software Carpentry](#software-carpentry)
- [SymPy](#sympy)

# Julia

## JuliaWeb: The Networking / Web framework for the [Julia Programming Language](http://www.julialang.org).

**Please ask questions [here](https://github.com/swcarpentry/gsoc2015/issues/9)**
or [here](https://github.com/JuliaWeb/Roadmap/issues).

Julia is a high-level, high-performance dynamic programming language for technical computing and has seen significant adoption in various fields/areas of practice. One of the current deficiencies in the language is the lack of a robust networking / data exchange framework for obtaining and exporting data using standard network protocols. Existing efforts have relied on unstable/minimally-supported external packages; as a result, there is an underlying fragility to the network and web stacks.

We would like to improve the robustness of the Julia network/web framework by initially focusing on the sound implementation of a TLS package that would underpin secure communications between Julia programs and the general internet community. It is our hope that the TLS package would be the official way to develop secure higher level network interfaces such as LDAPS, HTTPS, FTPS, etc. The non-secure versions of these interfaces/protocols will also need some work.

### Technical Details

Experience with networking and network protocols from OSI layers 3 (Network) through 7 (Application) will be required, as will an ability to read and understand relevant internet standards (RFCs). Familiarity with both Julia and C / C++ will also be required. Formal software development and support experience would be beneficial but is not a firm requirement.

### Mentors

* @sbromberger
* (a few more pending)

### Acknowledgements

* The entire Julia core team
* The members of [JuliaWeb](https://github.com/JuliaWeb)

# Software Carpentry

## Add taxonomic name resolution to the EcoData Retriever to facilitate data science approaches to ecology

**Please ask questions [here](https://github.com/swcarpentry/gsoc2015/issues/1).**

### Rationale

The [EcoData Retriever](http://ecodataretriever.org) is a Python based tool
for automatically downloading, cleaning up,
and restructuring ecological data. It does the hard work of data munging so
that scientists can focus on doing science.

One of the challenges of ecological (and evolutionary) data is that the
names of species are constantly being
redefined. This makes it difficult to combine datasets to do interesting
science. By automating reconciliation of
different species names as part of the process of accessing the data in the
first place it will become much easier
to combine diverse datasets and in new and interesting ways.

### Approach

This project would extendthe EcoData Retriever using Python to access one
or more of the existing web
services that reconcile species names
(e.g., [iPlant's Taxonomic
Name Resolution Service](http://tnrs.iplantcollaborative.org/TNRSapp.html))
and automatically replacing the species scientific names in the generated
databases. Specifically this
would involve:

* Object oriented programming in Python
* Using Python to query web service APIs

### Challenges

Scientific names are stored inconsistently across datasets, so it will be
necessary to either modifying the scripts
that hold information on each dataset to indicate the location of the
species information or use an existing ontology
to automatically identify the location.

### Involved toolkits or projects

* The [EcoData Retriever](http://ecodataretriever.org)
* Python
* The APIs for the taxonomic name resolution services.
* Relational database management systems (RDBMS) including MySQL,
PostgreSQL, SQLite

### Degree of difficulty and needed skills

* Moderate Difficulty
* Knowledge of Python
* Knowledge of interacting with web services via APIs is a plus, but could
be learned during the project

### Involved developer communities

The EcoData Retriever primarily interacts via issues and pull requests on
GitHub.

### Mentors

* @ethanwhite
* @bendmorris
* @sckott

## Improving reproducibility in science by adding provenance tracking to the EcoData Retriever

**Please ask questions [here](https://github.com/swcarpentry/gsoc2015/issues/2).**

### Rationale

The [EcoData Retriever](http://ecodataretriever.org) is a Python based tool
for automatically downloading, cleaning up,
and restructuring ecological data. It does the hard work of data munging so
that scientists can focus on doing science.

Science is experiencing a reproducibility crisis in that it is becoming
clear that published results often cannot be
reproduced. Part of the challenge of reproducibility in data science style
research is that most of the steps
related to data: downloading it, cleaning it up, restructuring it, are
either done manually or using one-off scripts
and therefore this phase of the scientific process is not reproducible. The
EcoData Retriever already solves many of
these problems, but it doesn't currently keep track of exactly what has
been done and therefore fails to support
full reproducible workflows.

### Approach

This project would extend the EcoData Retriever using Python to store all
of the metadata necessary for
full reproduction in an associated SQLite database.

Specifically this would involve:

* Object oriented programming in Python
* Design an SQLite database for storing provenance information or use an
existing framework (e.g,. http://code.google.com/p/core-provenance-library/)
* Implement checks to make sure that the data is in the same form created
by the Retriever when retrieving provenance information

### Involved toolkits or projects

* The [EcoData Retriever](http://ecodataretriever.org)
* Python
* Relational database management systems (RDBMS) including MySQL,
PostgreSQL, SQLite
* Potentially an existing provenance library

### Degree of difficulty and needed skills

* Moderate Difficulty
* Knowledge of Python
* Some experience with SQL

### Involved developer communities

The EcoData Retriever primarily interacts via issues and pull requests on
GitHub.

### Mentors

* @ethanwhite
* @bendmorris

## Write a result-aggregation server for the installation-test scripts

**Please as questions [here](https://github.com/swcarpentry/gsoc2015/issues/3).**

### Background

[Software Carpentry][swc] has [installation-test scripts][swc-install] so students can check
that they've successfully installed any software required by their workshop.
However, we don't collect the results of student tests, which makes a number of
things more difficult than they need to be.  Statistics about installed versions
would make it easy to:

* Figure out how much trouble our students are having with installation (for a
  given workshop or in general).
* Make informed decisions about deprecating older versions of our various
  dependencies (see swcarpentry/bc#724, swcarpentry/sql-novice-survey#13,
  swcarpentry/git-novice#32, and [here][git-novice-pull-comment]) or modernizing our lessons to
  catch up with current systems (see swcarpentry/workshop-template#157 and
  swcarpentry/workshop-template#159).

### Approach

This project would:

* Create a model for installed packages, failed package checks, and
  diagnostic system information.
* Design an API so clients can submit the results of their
  installation-test script.
* Write a small server to serve the API, store the results in a
  relational database, and allow administators to analyze the content.
* Update the installation-test scripts to (optionally) submit their
  results to the new server.

I'm not particular about the web framework you use to write the
server, but I have the most experience with [Django][] and
[Flask][].  If you prefer a different framework, I'm fine with
anything that takes care of the boilerplate and lets you focus on
the high-level tasks.

### Challenges

Designing and implementing a simple API for storing test results,
error messages, diagnostic system information, etc.  We want a
robust, flexible system that's small and easy to maintain going
forward.

### Involved toolkits or projects

* Python, for extending the existing installation test scripts.
* A web framework like [Django][], [Flask][], [RoR][], [Express][],
  ...
* Relational database management systems (RDBMS) including MySQL,
  PostgreSQL, SQLite.

### Degree of difficulty and needed skills

* Moderate difficulty.  This will be a simple server
  application, but you'll be designing and writing it from
  scratch.
* Knowledge of Python, to write client-side code for the
  installation test scripts.
* Knowledge of a web framework and basic API design.
* Knowledge of relational databases or a wrapping library
  for storing the results.

Any of these skills could be learned during the project,
but you probably can't learn *all* of them during the
project ;).

### Mentors

* @wking

### Acknowlegements

Thanks to @xuf12 for the initial idea behind this project.

## Amy: A Web-Based Tool for Managing Workshops

**Please ask questions [here](https://github.com/swcarpentry/gsoc2015/issues/6).**

[Software Carpentry][swc] workshops are currently managed by hand
using a complex (and fragile) mix that includes SQL files stored in GitHub,
regional mailing lists,
and other bits and pieces that have been cobbled together over the last five years.
Learning how to drive all of this takes a lot of time,
and is a major barrier to partner organizations getting more involved in workshop setup,
so we have started building [Amy][amy],
a Django application for managing workshops.
Basic functionality is in place,
but many features have not yet been implemented,
and it needs a lot of improvements in usability
(not to mention a lot more testing).

### Technical Details

Amy is a straightforward [Django][Django] application;
experience with that framework (and with Python) is required.
Some of the features we would like to add require Javascript,
so familiarity with [JQuery][jquery] and other frameworks is an asset.

Amy will manage personal identifying information,
so applicants should also have a basic understanding of security engineering.
Experience with deploying and maintaining applications is also an asset.

### Mentors

* @gvwilson
* @wking
* @r-gaia-cs

### Acknowledgments

Thanks to everyone who has helped get [Amy][amy] this far.

# SymPy

See the GSoC Ideas list on the SymPy Wiki:

https://github.com/sympy/sympy/wiki/GSoC-2015-Ideas

[swc]: https://github.com/swcarpentry/workshop-template/tree/gh-pages/setup
[swc-install]: https://github.com/wking/swc-setup-installation-test
[git-novice-pull-comment]: https://github.com/swcarpentry/git-novice/pull/43#issuecomment-74177654
[Django]: https://www.djangoproject.com/
[Flask]: http://flask.pocoo.org/
[RoR]: http://rubyonrails.org/
[Express]: http://expressjs.com/
[github]: https://github.com/swcarpentry
[discuss]: http://software-carpentry.org/pages/join.html
[irc]: http://www.mozillascience.org/join-the-sciencelab-on-irc
[amy]: http://github.com/swcarpentry/amy
[jquery]: http://jquery.com/
