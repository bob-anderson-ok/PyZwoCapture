PyZwoCapture
============

PyZwoCapture is a camera control and capture program for ZWO ASI cameras that have an ASCOM interface.

FITS files are used to record the video.

During recording, PyZwoCapture uses a serial connection to an Arduino based GPS flash-tag module 
to request goal-post flashes, one at the beginning, and another at the end. At completion of the 
recording, it processes those flashes automatically (it finds the leading edges of the flashes, 
interpolates the frame times, and assigns the GPS timestamps read from the GPS flasher to the start
and end flashes). During that processing, an analysis is performed of all the intervals between
frames to detect possible dropped frames or other deviations from a steady cadence. This process
results in GPS accurate timestamps being added to the DATE-OBS meta-data in each frames' FITS header.