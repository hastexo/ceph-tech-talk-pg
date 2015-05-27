The Parable of the
### obsessive-compulsive <!-- .element class="fragment" -->
## tennis coach


I have
## 5 students
Alice, Bob, Charlie, Daisy & Eric


I have
## 300 tennis balls


I want to
## distribute
them evenly among my students.


# How?


A simple approach:
## round robin


But my
# OCD
objects.


I want to distribute tennis balls
### reproducibly


So I
## number
all the tennis balls.


And apply a simple
## algorithm


### Modulo
# FTW!


## `71 % 5 = 1` <!-- .element class="fragment" -->
## `130 % 5 = 0`
## `213 % 5 = 3` <!-- .element class="fragment" -->


# Happy!
Until disaster strikes. <!-- .element class="fragment" -->


Another
## student
arrives.
# Frank
Uh-oh. <!-- .element class="fragment" -->


Well, maybe it's not that bad.


## `31 % 5 = 1`
## `31 % 6 = 1` <!-- .element class="fragment" -->
So we're cool, right? <!-- .element class="fragment" -->


## `36 % 5 = 1`
## `36 % 6 = 0` <!-- .element class="fragment" -->
All right, maybe not. <!-- .element class="fragment" -->


# Every
distributed storage system

has this
## problem


Just about every
### contemporary
distributed storage system

solves it
### the same way.


So what do we do?


We add
## buckets
to put the tennis balls into.


Let's say we have
# 60
buckets.


# Same
## algorithm


### `71 % 60 = 11` <!-- .element class="fragment" -->
### `130 % 60 = 10`
### `213 % 60 = 33` <!-- .element class="fragment" -->


Now we keep a
# list
of buckets per student.


We make the list available to
## everyone


If Frankie walks on, we move only
## buckets
and update the
## list


Everyone just gives up
# 2
of their 12 buckets.


At the end, everyone has
# 10


And suddenly, migration is
### proportional
to capacity change.


<!-- .slide: data-background-image="images/ceph-logo.svg" data-background-size="contain" -->
### Tennis balls
## ==
## RADOS objects


<!-- .slide: data-background-image="images/ceph-logo.svg" data-background-size="contain" -->
### Numerical IDs
## ==
## Object hashes


<!-- .slide: data-background-image="images/ceph-logo.svg" data-background-size="contain" -->
### Buckets
## ==
## Placement Groups


<!-- .slide: data-background-image="images/ceph-logo.svg" data-background-size="contain" -->
### Students
## ==
## OSDs


<!-- .slide: data-background-image="images/ceph-logo.svg" data-background-size="contain" -->
### List
## ==
## OSD Map


The map changes
# only
when the storage topology changes


And is
# lazily
propagated throughout the system


This is way more
### effective
### efficient
### scaleable
than central data lookups.