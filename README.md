taglib-ruby
===========

Ruby interface for the [TagLib C++ library][taglib].

In contrast to other libraries, this one wraps the full C++ API using
SWIG, not only the minimal C API. This means that all tags can be
accessed.

taglib-ruby is work in progress, here are some of the things still left
to do (contributors very welcome):

* Pre-compiled Gem for Windows
* More coverage of the library besides ID3v2

Usage
-----

    require 'taglib'

    # Load an ID3v2 tag from a file
    file = TagLib::MPEG::File.new("wake_up.mp3")
    tag = file.id3v2_tag

    # Read basic attributes
    tag.title  #=> "Wake Up"
    tag.artist  #=> "Arcade Fire"
    tag.track  #=> 7

    # Access all frames
    tag.frame_list.size  #=> 13

    # Track frame
    track = tag.frame_list("TRCK").first
    track.to_s  #=> "7/10"

    # Attached picture frame
    cover = tag.frame_list("APIC").first
    cover.mime_type  #=> "image/jpeg"
    cover.picture  #=> "\xFF\xD8\xFF\xE0\x00\x10JFIF..."

Contributing
------------

* Check out the latest master to make sure the feature hasn't been
  implemented or the bug hasn't been fixed yet
* Check out the issue tracker to make sure someone already hasn't
  requested it and/or contributed it
* Fork the project
* Start a feature/bugfix branch
* Commit and push until you are happy with your contribution
* Make sure to add tests for it. This is important so I don't break it
  in a future version unintentionally.
* Please try not to mess with the Rakefile, version, or history. If you
  want to have your own version, or is otherwise necessary, that is
  fine, but please isolate to its own commit so I can cherry-pick around
  it.

License
-------

taglib-ruby is distributed under the MIT License,
see LICENSE.txt for details.

Copyright (c) 2010, 2011 Robin Stocker.

[taglib]: http://developer.kde.org/~wheeler/taglib.html