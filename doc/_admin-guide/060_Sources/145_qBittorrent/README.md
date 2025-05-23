---
title: qBittorrent log source
short_title: qbittorrent
id: adm-src-qbit
description: >-
    In {{ site.product.short_name }} 4.6 and later versions it is possible to collect logs of the qBittorrent application.
---

```config
source s_qbittorrent {
  qbittorrent(
    dir("/path/to/qbittorrent-root-log-dir")
  );
};
```

To configure the source, specify the root log directory of qBittorrent in the `dir()` parameter. The root log directory can be accessed by selecting **Tools** &#62; **Preferences** &#62; **Behavior** &#62; **Log file** &#62; **Save path** in the qBittorrent application. Otherwise, the `qbittorrent()` source has the same parameters as the [[file() source|adm-src-file-opt]].

The `qbittorrent()` driver is a reusable configuration snippet. For details on using or writing such configuration snippets, see Reusing configuration blocks. The source of the qBittorrent configuration snippet can be accessed on GitHub.
