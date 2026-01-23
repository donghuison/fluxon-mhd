## Release notes

Full release notes can be found in the GitHub history of releases.
  
RELEASE NOTES FOR v2.3 (26-May-2023):
  - Updated for compatibility with newer versions of PDL
  - Organization of solar wind processing codes
  - Development of automated processing module
  - Other consolidated changes and closing of branches

RELEASE NOTES FOR v2.2 (22-Nov-2008):
  - Mass is actively tracked in the data structures
  - Binary save files are supported; all files are auto-gzipped if they have a '.gz' extension
  - First-stage parallelization appears functional -- the code can spawn to make use of multiple CPU cores on the local machine.
  - Interpolation of all scientific values onto arbitrary locations is now possible.
  - New reconnection criteria make reconnection "in the wrong direction" much less common.
  - Multiple bug fixes in the perl interface code
  - Data structure labels can now be edited via the perl hash interface.
  - There is better support for motion and interaction of flux concentrations.

RELEASE NOTES FOR v2.1 (3-Apr-2008):
  - Many, many bug fixes
  - Photospheres and other refs handled correctly by hash interface
  - Reworked Perl hash interface to eliminate stale pointers altogether
  - Added Hilbert ditherer
  - Better reconnection support
  - Better auto-open support

RELEASE NOTES FOR v2.0 (1-Nov-2007):
  - Now includes reconnection via the "reconnect" Flux::World method
  - Updated and validated force laws
  - Full plasmoid support
  - Full open-field boundary support, including omega and U loop interactions with the boundary
  - Includes a Floyd-Steinberg ditherer for footpoint placement
  - Includes techniques ("ductions") for moving footpoints in time-dependent simulations
  - Better control over relaxation parameters
  - Emergence/cancellation support
  - Better interaction with Perl:
	- Support for all fields via the Perl hash interface
	- No memory leaks
	- No stale pointers