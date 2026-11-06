# proxy-project.github.io

Public pages for the Spending app. The app code lives in a private repo.

## bank-return/

Served at https://proxy-project.github.io/bank-return/, the redirect URL
registered with Enable Banking.

Enable Banking only redirects to https addresses. After a bank approval it
sends the browser here with `code` and `state`. The page reads the app's
address from the part of `state` after the last dot, accepts it only when it
is on a private network (`localhost`, `*.local`, `10.x`, `172.16.x` to
`172.31.x`, `192.168.x`, `100.64.x` to `100.127.x`) and moves the browser to
`<app>/callback`, passing on only `code`, `state`, `error` and
`error_description`.

The page has no server side, loads nothing from other sites and stores
nothing. The approval code is useless without the app's private key.

The source of truth is `relay/index.html` in the app repo. Copy it here when
it changes.
