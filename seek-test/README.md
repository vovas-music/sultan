# Seek test

A page that plays this song four ways — the MP3 copy, the FLAC master, the
FLAC rewrapped in MP4 (`sultan.mp4`) served by Pages as `audio/mp4`, and the
site's own MP4 served by raw.githubusercontent.com as
`application/octet-stream` — with jumps to 1:00, 3:00 and 20 s
before the end, and a switch to the next file at the same second. It logs the
element's events and the browser's `canPlayType` answers.

It was built to find out why vovazakharov.com's player landed early when
seeking on an iPhone
([vzakharov/vovazakharov.com#157](https://github.com/vzakharov/vovazakharov.com/pull/157)).
On iPhone Safari (iOS 18.7, Safari 26.6.1) the MP4 landed exactly where the
MP3 did. The FLAC, even with a one-second SEEKTABLE, landed nowhere near the
target from a cold load. AVFoundation seeks a bare FLAC by estimate, and it
seeks MP4's sample index exactly.

To run it again: Settings → Pages → Deploy from a branch → `main`, `/ (root)`,
then open `https://vovas-music.github.io/sultan/seek-test/`. Switch Pages off
afterwards.
