# Printer

https://www.openprinting.org/printers
PDL - page description laguage, used by printer

PDL
* PCL - hewlett-packard's printer command language
* Postscript - adobe systems first PDL
* PDF - adobe systems portable document format

CUPS - Common Unix Printing System
1. It accepts input in ASCII, PDF, HP/GL and raster image formats
2. Runs them through a filter that transforms the data stream into Postscript
3. Then passes postscript to a software layer that converts the data to a rasterized format
   that can be converted by various drivers to printer-specific language formats.
4. The data stream passed to the back-end filters that transfer the printer commands to the printers

`/var/spool` - data for later processing
`/var/spool/cups` - data about printing jobs
`/var/spool/lpd` - contains a subdirectory for each printer. Used only to store lock files,
to prevent multiple overlapping attempts to access each printer


