# Boise math circles

This is the source repository for the draft Boise math circles home page, [beta.boisemathcircles.org](http://beta.boisemathcircles.org).

## To create a session post

The text of the post and several other optional components are located in different folders, and tied together using concomitant file naming.

The **text** of the post should be placed in either `bmc-sessions/\_posts` or in `bmtc-sessions/\_posts`. The file name should be `yyyy-mm-dd-some-name.md` (or use `.html` if you prefer). The topmatter of the file must include the title variable, and optionally may include a tags variable.

    ---
    title: My session title
    tags: incidence-geometry projective-plane
    ---

An optional **header image** may be placed in `assets/headers`. The base of the file name should be exactly the same as the base of the post, for instance, `yyyy-mm-dd-some-name.jpg`. The images will be scaled down to 300x500, so try to keep them small (less than 50-100k).

Any number of optional **handouts** may be placed in a folder in `assets/handouts`. The name of the folder should be exactly the same as the base of the post, for instance, `yyyy-mm-dd-some-name/`. Please host large handouts elsewhere or reduce the file size. The handouts can be included in the post as a `<ul>` with the command `{% include handouts.html %}`. The order will be the default and the filename will become the link text. Of course you may also link to them manually.

Additional images and attachments may be placed elsewhere in `assets`, such as in `assets/misc`. These may be linked to manually. Again please host large files, such as high-res photos, elsewhere. Google drive and google photos are good options.