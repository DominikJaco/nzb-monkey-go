# NZB Monkey Go

A completely rewritten version in Golang of the [NZB Monkey](https://github.com/nzblnk/nzb-monkey), the reference implementation written in Python of how to handle a [NZBLNK](https://nzblnk.github.io/)-URI.
NZB Monkey Go also includes the functionality of the [NZBSearcher](https://github.com/Tensai75/nzbsearcher) so besides in the nzb search engines it can also search directly on the news server and create the NZB file from the article headers.

## Running the Monkey

Running the NZB Monkey Go is virtually identical to running the NZB Monkey.
See detailed information [here](https://nzblnk.github.io/nzb-monkey/).

Differences are that in the config.txt file, 'directsearch' can be enabled as an additional search engine in the section 'SEARCHENGINES' and an additional section 'DIRECTSEARCH' is included, required for the direct search on the news server to work.

Note that directsearch requires the NZBLNK to include the news groups (parameter 'g') and an additional parameter for the date ('d') when the post was uploaded to the Usenet.
Parameter 'd' can be provided either in the format 'DD.MM.YYYY' or as an unix timestamp.

![Monkey-Gif](https://github.com/Tensai75/nzb-monkey-go/raw/main/resources/nzbmonkey-go.gif)

## Windows and Linux binaries

The binaries are available on the [release page](https://github.com/Tensai75/nzb-monkey-go/releases).

The linux binary must be chmoded to be executable before it can be started.

### macOS Support

A macOS binary is provided on the [release page](https://github.com/Tensai75/nzb-monkey-go/releases) as well, however the program cannot register the nzblnk URI protocol itself.
On the NZB Monkey github some solutions on how to register the protocol have been [discussed](https://github.com/nzblnk/nzb-monkey/issues/20) which should work for the NZB Monkey Go as well.

Please also note that the macOS binary is neither signed nor executable.

## Contribution

Feel free to send pull requests.

## Change log

#### v0.1.0-beta4
- Fix panic on NNTP connection errors and empty connectionGuard channel if no connection was established.

#### v0.1.0-beta3
- directsearch: new configuration parameter "skip" (default true). If set to true directsearch is skipped if a valid NZB file was already found.
- Fix for the message scan getting stuck on errors.
- Fix for incorrect parsing of the configuration file for values containing a "#" character.
- Reduced default threshold for missing files and segments.

#### v0.1.0-beta2
- Waiting time before exiting the programme is now configurable
- directsearch: Change of the configurable time span for the search backwards from days to hours.

  If the parameter date is specified as Unix timestamp, the search starts from date minus the configured number of hours and goes up to date plus 1 hour (as buffer).
  If the parameter date is specified as DD.MM.YYYY, the search will cover the whole day plus the configured number of hours of the previous day.

- Bug fixes and elimination of race conditions

#### v0.1.0-beta1
- first public release