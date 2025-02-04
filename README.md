# OpenBSD ports

Personal collection of OpenBSD ports.

-   [databases/badger](databases/badger/) - Tools to manage Badger database.
-   [mail/alps](mail/alps/) - Simple and extensible webmail.
-   [mail/opensmtpd-filter-clamav](mail/opensmtpd-filters/clamav/) - ClamAV
    integration to the OpenSMTPD daemon.
-   [multimedia/serviio](multimedia/serviio/) - Free media server.
-   [net/go-shadowsocks2](net/go-shadowsocks2/) - Modern shadowsocks in Go.
-   [productivity/tokidoki](productivity/tokidoki/) - Small and robust calendar
    & contacts server.
-   [sysutils/aggy](sysutils/aggy/) - IPV4 subnet aggregator.
-   [sysutils/pf-badhost](sysutils/pf-badhost/) - Fast, bi-directional network
    filtering utility.
-   [sysutils/pistol](sysutils/pistol/) - General purpose file previewer.
-   [textproc/go-chroma](textproc/go-chroma/) - General purpose syntax
    highlighter in pure Go.
-   [textproc/minify](textproc/minify/) - Minifiers for web formats.

## Usage

Copy/merge this repository into `/usr/ports/mystuff` then run `make install`
inside the directory of the desired port to install it locally or `make package`
to create a distributable package.

## Contributing

Any contributions are welcome - see the
[CONTRIBUTING.md](.github/CONTRIBUTING.md) file for details.
