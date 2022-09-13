# RequestAndResponseLoggingFilter
Spring Web filter for logging request and response
forked gist.github.com/int128/e47217bebdb4c402b2ffa7cc199307ba

## probrem
original gist https://gist.github.com/int128/e47217bebdb4c402b2ffa7cc199307ba

There was a problem of garbled characters in json.
The reason is follows.

- RFC8259 requires UTF-8 encoding for JSON
- Accordingly, no character set is specified for Content-Type: application/json
- Spring Boot has also changed in that way since 2.2
- In the original "RequestAndResponseLoggingFilter.java", if the character set is not specified, it will be ISO-8859-1.

## changes
Changed to consider ISO-8859-1(Latain-1) as UTF-8 when Content-Type: application/json.
