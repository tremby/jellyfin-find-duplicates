# jellyfin-find-duplicates

Find duplicate TV show episodes in a Jellyfin library.

## Usage

    jellyfin-find-duplicates [-h] [--help]

Information is output about any duplicate episodes found.
If the program exits with no output and a success status,
no duplicates were found.

### Options

- `-h`, `--help`: Show help text

### Example output

```
Series "The Itchy and Scratchy Show" has duplicates:
  The Itchy and Scratchy Show S01E01
  - 1990-01-28T19:42:33-05:00: \\disk\shows\The Itchy and Scratchy Show\Season 01\The.Itchy.And.Scratchy.Show.S01E01.1080p.WEB.H264-MUNTZ.mkv
  - 1990-01-28T20:01:42-05:00: \\disk\shows\The Itchy and Scratchy Show\Season 01\the.itchy.and.scratchy.show.s01e01.proper.1080p.web-dl.h264-elbarto.mkv
  The Itchy and Scratchy Show S01E04
  - 1990-10-11T19:50:01-04:00: \\disk\shows\The Itchy and Scratchy Show\Season 01\The.Itchy.And.Scratchy.Show.S01E04.720p.HDTV.H.264.mPRiNCE.mkv
  - 1990-10-11T20:09:22-04:00: \\disk\shows\The Itchy and Scratchy Show\Season 01\the.itchy.and.scratchy.show.s01e04.1080p.web-dl.h264-elbarto.mkv
Series "Single Female Lawyer" has duplicates:
  Single Female Lawyer S01E01
  - 1999-11-07T20:00:05-05:00: \\disk\shows\Single Female Lawyer\Season 01\Single.Female.Lawyer.S01E01.480p.NTSC.h264-LRRR.mkv
  - 2000-01-22T14:17:06-05:00: \\disk\shows\Single Female Lawyer\Single.Female.Lawyer.S01.480p.NTSC.h264-LRRR\Single.Female.Lawyer.S01E01.480p.NTSC.h264-LRRR.mkv
  Single Female Lawyer S01E02
  - 1999-11-14T20:04:30-05:00: \\disk\shows\Single Female Lawyer\Season 01\Single.Female.Lawyer.S01E02.480p.NTSC.h264-LRRR.mkv
  - 2000-01-22T14:17:06-05:00: \\disk\shows\Single Female Lawyer\Single.Female.Lawyer.S01.480p.NTSC.h264-LRRR\Single.Female.Lawyer.S01E02.480p.NTSC.h264-LRRR.mkv
  Single Female Lawyer S01E03
  - 1999-11-21T19:48:50-05:00: \\disk\shows\Single Female Lawyer\Season 01\Single.Female.Lawyer.S01E03.480p.NTSC.h264-LRRR.mkv
  - 2000-01-22T14:17:06-05:00: \\disk\shows\Single Female Lawyer\Single.Female.Lawyer.S01.480p.NTSC.h264-LRRR\Single.Female.Lawyer.S01E03.480p.NTSC.h264-LRRR.mkv
```

## Configuration

The file `$XDG_CONFIG_HOME/jellyfin-find-duplicates.conf`
(which is usually `~/.config/jellyfin-find-duplicates.conf`)
is sourced as a bash script if it exists.

An example is distributed as `jellyfin-find-duplicates.conf.example`
it can be copied into place with

    cp jellyfin-find-duplicates.conf.example $XDG_CONFIG_HOME/jellyfin-find-duplicates.conf

and then edited.

The following variables are then expected to exist:

- `JELLYFIN_HOST`
  The Jellyfin URL scheme and hostname for the server,
  with no trailing slash.
  Example: `https://jellyfin.local`
- `JELLYFIN_TOKEN`:
  The Jellyfin API token.
  One can be made via the Jellyfin dashboard, at "Advanced" → "API Keys".
  Example: `abc123abc123`
- `JELLYFIN_USER`:
  The name of the Jellyfin user to use as context.
  Example: `bob`
- `JELLYFIN_SHOWS_LIB_NAME`:
  The name of the TV shows library in Jellyfin.
  Example: `Shows`

## Dependencies

- `curl`, which you probably have. If not, it is in every package manager.
  Run `apt install curl` or equivalent.
- `jq`, the JSON toolkit, which you may not have.
  Run `apt install jq` or equivalent.

## Compatibility

So far this is only tested on Linux.
It may work on other platforms.

## Contributing

Patches welcome.

Ideas:

- Improve speed
- Improve output
- Also notice any missing episodes
