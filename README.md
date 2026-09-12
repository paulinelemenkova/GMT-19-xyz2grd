# GMT xyz2grd — Direct XYZ-to-Grid Conversion and Contour Map

A GMT (Generic Mapping Tools) shell script that converts a regularly-spaced XYZ point table directly into a NetCDF grid using the xyz2grd module and contour-maps the result. Unlike interpolating gridders, xyz2grd performs an exact conversion: each grid node is filled from the matching table value, so it is the appropriate tool when the input data already lie on a regular lattice. The example covers the Kuril-Kamchatka Trench and supports figures in the author's marine-geophysical and cartographic publications.

## What the script does

- inspect the XYZ data range (gmtinfo)
- convert the ASCII XYZ table to binary for speed (gmt convert)
- convert the regular XYZ table directly to a NetCDF grid with the region and increment set (xyz2grd -R -I)
- contour the resulting grid (grdcontour)
- add coastlines, frame, scale bar and directional rose (pscoast, psbasemap)
- add annotations (pstext) and the GMT logo (logo)
- export to raster (psconvert) at high resolution

This is the direct-conversion counterpart to the interpolating gridders (surface, nearneighbor): use xyz2grd when the data are already gridded, and the interpolating modules when they are scattered.

## Data source

Regularly-spaced XYZ bathymetry exported from a global grid (e.g. TOPEX/UCSD). Input as an ASCII .xyz table.

## Requirements

- GMT 6.x (Generic Mapping Tools): https://www.generic-mapping-tools.org
- A POSIX shell (bash/sh)
- The XYZ point table available locally

## Usage

Place the required XYZ table in the working directory, adjust the -R region and -I increment at the top of the script, then run:

    bash GMT-22-script-JM-xyz2grd.sh

The script writes a PostScript file and converts it to a raster image (JPG/PNG) via psconvert.

## Author and citation

Polina Lemenkova
ORCID: https://orcid.org/0000-0002-5759-1089

This script supports figures in the author's marine-geophysical and cartographic papers; please cite the specific article a given figure appears in. The full publication list is available via the ORCID record above.

## License

See the LICENSE file in this repository.
