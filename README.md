Subs: A lightweight alternative to Ruby gems
============================================

Overview
--------

There are often cases when a developer/team needs to reuse and share portions of code which just "aren't enough" for a gem. Subs might be a solution to this problem. Read on.

The name "subs", the concept of subs, the technology behind subs are yet experimental. All sorts of feedback is highly appreciated.

Examples of subs
----------------

* A library or extension in its early stage of existence with a high reuse potential.
* A low-level extension to a  class which implements a particular pattern, which isn't enough for a gem. Examples: boilerplate initializer, attribute validation, attribute caching etc.

Sub features
------------

1. Subs are truly **lightweight**. 
  1. Subs **don't have version numbers**.
  2. Subs **don't have init code**. They won't gain control until you `require` them.
  3. The amount of **formalities** required to update a sub **is almost zero**.
  4. There is **no minimum amount of code** required to make a sub. If your extension is 1 line long, but is reusable &mdash; go make a sub of it.
2. Subs do have **home repositories**, but updates to subs are made **directly in the projects which use them**.
  1. Sub's home repository is **checked out to N locations simultaneously**.
  2. After you've made an update to the sub **commit your changes right away** to the sub's `origin`.
3. Underlying **mechanism** to manage the distribution of subs is **Git submodules**.
4. Subs are often **local to developer/team** which produced them.
  1. Subs **don't require unique names** like gems do. It's okay to name your sub `downloader` if you can uniquely identify what it is.
5. Subs **must have full test coverage**. This is to compensate for their highly dynamic and version-free nature.

Installation
------------

Consider you are in the local working copy of your project and you want to install a sub from https://github.com/dadooda/feature_cache into it. Steps follow.

1. Create a directory for subs:

    ```sh
    $ mkdir -p vendor/subs
    ```

2. Check out a Git submodule:

    ```sh
    $ git submodule add git@github.com:dadooda/feature_cache vendor/subs/feature_cache
    ```

3. Add the `$:` include path update to your boot code, e.g. in your `boot.rb`:

    ```ruby
    Dir[File.expand_path("../vendor/subs/*/lib", __FILE__)].each {|fn| $: << fn if File.directory?(fn)}
    ```

4. Now you can use the library anywhere in your code:

    ```ruby
    require "feature/cache"
    ```

5. To update all installed subs to their latest versions, do a:

    ```sh
    $ git submodule update --init --remote
    ```

