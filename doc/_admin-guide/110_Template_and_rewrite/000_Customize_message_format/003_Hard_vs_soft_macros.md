---
title: Hard versus soft macros
id: adm-temp-hard-soft-macro
description: >-
    Hard macros contain data that is directly derived from the log message,
    for example, the ${MONTH} macro derives its value from the timestamp.
    Hard macros are read-only. Soft macros (sometimes also called name-value
    pairs) are either built-in macros automatically generated from the log
    message (for example, ${HOST}), or custom user-created macros generated
    by using the {{ site.product.short_name }} pattern database or a CSV-parser. In contrast to
    hard macros, soft macros are writable and can be modified within
    {{ site.product.short_name }}, for example, using rewrite rules.
---

Hard and soft macros are rather similar and often treated as equivalent.
Macros are most commonly used in filters and templates, which does not
modify the value of the macro, so both soft and hard macros can be used.
However, it is not possible to change the values of hard macros in
rewrite rules or via any other means.

The following macros in {{ site.product.short_name }} are hard macros and cannot be
modified: ${BSDTAG}, ${CONTEXT_ID}, ${DATE}, ${DAY}, ${FACILITY_NUM}, ${FACILITY},
${FULLDATE}, ${HOUR}, ${ISODATE}, ${ISOWEEK}, ${LEVEL_NUM}, ${LEVEL}, ${MIN}, ${MONTH_ABBREV},
${MONTH_NAME}, ${MONTH}, ${MONTH_WEEK}, ${PRIORITY}, ${PRI}, ${RCPTID}, ${SDATA}, ${SEC},
${SEQNUM}, ${SOURCEIP}, ${STAMP}, ${TAG}, ${TAGS}, ${TZOFFSET}, ${TZ}, ${UNIXTIME},
${WEEK_DAY_ABBREV}, ${WEEK_DAY_NAME}, ${WEEK_DAY}, ${WEEK}, ${YEAR_DAY}, ${YEAR}.

The following macros can be modified: ${FULLHOST_FROM}, ${FULLHOST},
${HOST_FROM}, ${HOST}, ${LEGACY_MSGHDR}, ${MESSAGE}, ${MSG}, ${MSGID}, ${MSGONLY}, ${PID},
${PROGRAM}, ${SOURCE}. Custom values created using rewrite rules or parsers
can be modified as well, just like stored matches of regular expressions
($0 \... $255).

Note that you can modify the timezone of the message, and change the
timezone-related macros that way. For details, see
Rewrite the timezone of a message.
