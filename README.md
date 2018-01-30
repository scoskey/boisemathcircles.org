# Boise math circles site source

This is the source repository for the draft Boise math circles home page, [beta.boisemathcircles.org](http://beta.boisemathcircles.org).

## To create session posts

The text of the post and several other optional components are located in different folders, and tied together using concomitant file naming.

The **text** of the post should be placed in either `bmc-sessions/\_posts` or in `bmtc-sessions/\_posts`. The file name should be `yyyy-mm-dd-session-id.md` or `yyyy-mm-dd-session-id.html`, where yyyy-mm-dd is the date of the session itself. Put the title and optionally some tags in the topmatter:

    ---
    title: My session title
    tags: incidence-geometry projective-plane
    ---

An optional **header image** may be placed in `assets/headers`. The base of the file name should be exactly the same as the base of the post, for instance, `yyyy-mm-dd-session-id.jpg`. Use small header images (less than 50&ndash;100k) as they will be scaled down to 300x500 anyway.

Any number of optional **handouts** may be placed in a folder in `assets/handouts`. The name of the folder should be exactly the same as the base of the post, for instance, `yyyy-mm-dd-session-id/`. Please host large handouts elsewhere or reduce the file size. The handouts can be included in the post as a `<ul>` with the command `{% include handouts.html %}`. The order will be alphabetical and the filename will become the link text. Of course you may also link to them manually using the target `"/assets/handouts/yyyy-mm-dd-session-id/The Handout.pdf"`.

Additional images and attachments may be placed elsewhere in `assets`, such as in `assets/misc`. These must be linked to manually. Again please host large files, such as full resolution photos, elsewhere. Google drive and google photos are good options.

## To edit pages

You can add to or update the content on the home page by editing `index.html`. The other pages are in the root folder with `.md` file extensions.

## To create pages

You can create pages `my-page.md` or `my-page.html` in the base folder. Put the title and the layout line in the topmatter:

    ---
    title: My page title
    layout: page
    ---

You can then link to the page using the target `"/my-page"`.

## To use styles

Style additions and overrides may be placed in `assets/main.scss` or at the top of a particular post or page using `<style></style>`.