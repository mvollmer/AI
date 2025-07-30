My experience with using Cursor to do some non-trivial refactoring of
cockpit-machines.

- Downloaded 150 MB of binary-only, proprietary software from a random
  link given to me on chat and ran it on my personal computer without
  any extra isolation. This is a brave new world for me.

- Please Cursor people, make a flatpak.

- 2 hours of refactoring in the morning was surprisingly fun. I was
  trying to renovate the use of virt-xml in cockpit-machines, and I
  had a pretty good plan in my head (or so I thought).

- Cursor helped me remember/figure out all the sprawling changes that
  needed to be made across the code base to make this a global
  improvement.

- Didn't test the code, but everything looked correct. Nothing
  obviously broken.

- Had to prompt and prompt and prompt to get an acceptable result, but
  it was not frustrating. Sometimes I deliberately used minimal
  prompts like "Do the same kind of change globally." and the result
  was correct but not what I wanted. A more precise prompt did the
  trick. Can't expect the machine to read my mind yet. Voice
  recognition would maybe be good to gain some speed.

- Had to prompt and guide to produce quality code without obvious and
  massive duplications, but it was straightforward.

- Felt sluggish and not really faster in the end.  The machine was
  thinking and planning and churning for minutes at a time for a
  modest amount of changes.

- As a point of comparison: Search/replace by hand is obviously,
  massively, and unspeakably slower than search/replace by machines.
  Refactoring code to change the order of arguments of a function with
  Cursor is maybe kinda a bit faster than by hand.  It's not even
  close to the speedups that we have learned to expect from
  machines. A reasonable dedicated refactor tool would be considered
  unusable if would be only as fast as Cursor.

- The 2 hours of (in the end very mild) refactoring used 46 "requests"
  of my 500 requests per month. Thus, I get about 20 hours of vibing
  per month, or about 1 to 1.5 hours per day.  I have to use this
  sparingly if these numbers are correct.

- The generated code wasn't great, and I don't think I would let
  Cursor write new features for cockpit-machines.

The whole chat is [here](./cursor_what_is_the_project_license.md).

Comments on the prompts and their results are
[here](cursor_what_is_the_project_license_commented.md).
