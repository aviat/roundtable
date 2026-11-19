# Roundtable

A shared countdown timer and question board for meetings. Live at
**https://aviat.github.io/roundtable/**.

Start a meeting, share the link, and everyone with it sees the same timer and
questions: ask, upvote, reply, and mark questions answered. Press `?` in the app
for keyboard shortcuts.

## How it works

It's a single static page (`index.html`) with no backend and no build step.

- The meeting ID lives in the URL fragment (`#...`), which browsers never send
  to the server.
- Browsers find each other through public Nostr relays
  ([Trystero](https://github.com/dmotz/trystero)), then sync over WebRTC.
  Signaling is encrypted with the meeting ID.
- Every edit carries a timestamp and merges last-writer-wins, so peers converge
  whatever order messages arrive in. Each browser also keeps a copy in
  `localStorage`.

## Run it locally

```sh
python3 -m http.server 8000
# open http://localhost:8000/
```

Open the same meeting link in two tabs to see the sync.

## Contributing

PRs are welcome. Keep it a single dependency-free page, and test in two
browser tabs before opening a PR.
