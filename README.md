Subs: A lightweight alternative to Ruby gems
============================================

Introduction
------------

There are often cases when a developer/team need to reuse and share portions of code which just "aren't enough" for a gem. Subs might be a solution to this problem. Read on.

The name "subs", the concept of subs, the technology behind subs are yet experimental. All sorts of feedback is highly appreciated.

Examples of subs
----------------

* A library or extension in its early stage of existence with a high reuse potential.
* A low-level extension to a  class which implements a particular pattern, which isn't enough for a gem. Examples: boilerplate initializer, attribute validation, attribute caching etc.

Sub features
------------

1. Subs are truly **lightweight**. 
  1. Subs **don't have version numbers**.
  2. The amount of **formalities** required to update a sub **is almost zero**.
  3. There is **no minimum amount of code** required to make a sub. If your extension is 1 line long, but is reusable -- go make a sub of it.
2. Subs do have **home repositories**, but updates to subs are made **directly in the projects which use them**.
  1. Sub's home repository is **checked out to N locations simultaneously**.
  2. **Don't forget to commit** your (semi-)working changes to the sub's home repository.
3. Underlying **mechanism** to manage the distribution of subs is **Git submodules**.
4. Subs are often **local to developer/team** which produced them.
  1. Subs **don't require unique names** like gems do. It's okay to name your sub `Downloader` if you can uniquely identify what it is.
5. Subs **must have full test coverage**. This is to compensate for their highly dynamic and version-free nature.
