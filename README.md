# FAD image viewer

FAD (fetch and display) image viewer is a simple Perl script for
fetching an image from an URL, and displaying it.

Certain image serving sites have a tendency to encourage people to
share, resulting in links you may not wish to open in a browser, but
rather in an image viewer.

This tool was written to accomodate one such popular site, where it is
possible to share both direct image download links, but also links to
an image viewing page. The image viewing page URL can be parsed to
fetch the actual image, but you need to guess whether it's a JPEG or a
PNG, or whether the file suffix is .jpg, .jpeg, or .png.

This tool takes care of that to a certain extent.

## Requirements

 - A unix-like desktop UI
 - Perl v5.10 or newer
 - cURL binary placed in `/usr/bin/curl`
 - EOG (Eye of GNOME) image viewer in `/usr/bin/eog`
 
## Configuration
 
In the first version, configuration is done inline, and not in a
separate configuration file.

### Configurable variables

| Variable | Default | Description |
| --- | --- | --- |
| `$fetcher` | `/usr/bin/curl` | cURL executable's path |
| `$viewer`  | `/usr/bin/eog`  | EOG executable's path  |
| `$directprefix` | `https://i.` | Prefix for links containing direct downloadable images |
| `$tmpdir` | `/tmp` | Temporary directory for storing downloaded images |

## Limitations, issues and improvements

This is a very simple tool. It only cares about JPEG and PNG files. It
was written with one specific service in mind, but will work with
other services that work similarly.

The tool does not clean up the temporary directory, and it does not
create its own subdirectory in the temporary directory. It assumes the
temporary directory exists. This could use some improvement.

If you use ctrl+c or other interrupts to kill the image viewer, FAD
will give you an error message about not being able to display the
image. Use the built-in quit command instead (in EOG: ctrl+q).

Other limitations are not described here, but there are sure to be
plenty.

This is meant to be a tiny tool, not a world problem solver.

If you want to improve on this script, I appreciate pull requests, but
please try to keep the code changes small if you want the pull
requests accepted.
