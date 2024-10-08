---
title: level() or priority()
id: adm-log-filters-level
description: >-
    This section describes level() filter function in {{ site.product.short_name }}.
---

*Synopsis:* level(\<priority-level\>) or level(\<priority-level\>..\<priority-level\>)

*Description:* The [[level() filter|adm-log-filters-level]] selects messages corresponding to a
single importance level, or a level-range. To select messages of a
specific level, use the name of the level as a filter parameter, for
example, use the following to select warning messages:

```config
level(warning)
```

To select a range of levels, include the beginning and the ending level
in the filter, separated with two dots (..). For example, to select
every message of error or higher level, use the following filter:

```config
level(err..emerg)
```
{% include doc/admin-guide/warnings/dotdot-stringonly.md %}

The [[level() filter|adm-log-filters-level]] accepts the following levels:

{% include doc/admin-guide/options/filter-severity.md %}
