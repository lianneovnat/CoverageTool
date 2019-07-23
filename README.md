# CoverageTool
A semi­automated graphic software – applications for plant phenotyping Lianne Merchuk-Ovnat, Ph.D.; Zev Ovnat; Orit Amir-Segev; Yaarit Kutsher; Yehoshua Saranga; Moshe Reuveni Plant Methods
'Coverage.exe' - instructions for use				
==================================				
"o  To exclude everything but the interior of a quadrilateral, position cursor over its 4 vertices and click F1, F2, F3 & F4 in clockwise order:"				
"at top left click F1, at top right click F2, at bottom right click F3, at bottom left click F4."				
"o  Click on radio button 1-10 to select colors to take into account (""Include"") and those to dis-count (""Ignore"")."				
o  Not all 10 + 10 selctions need be filled. The unused ones will have 'Include' and 'Ignore' with a black background.				
o  To select a color to include for one of the 10 selections - left click the color.				
o  To select a color to ignore for one of the 10 selections - shift-left click the color.				
"o  To reset a selection, first click the selection's button, then - right click anywhere in the image."				
o  Note: black is automatically ignored - so it need not be selected.				
"o  Note: the current selection set is automatically saved as 'Current' upon exit or clicking 'Selection'. So, useful 'Current' selections should be assigned a unique name with ""Saved As"" in the ""Selection"" dialog - so as not to be overwritten..."				
o  The calculation is as follows: 				
   - Let N be the number of pixels in the image.				
   - Let C be the number of pixels that were near to one of the selected colors to include.				
   - Let I be the number of pixels that were near to one of the selected colors to ignore.				
   - The result is: (C x 100) / (N - I)				
"   - If B is the number of Background pixels, then B = N - C - I"				
   - Thus the result is also: (C x 100) / (C + B)				
o  Select RGB or YCbCr for the color comparison method.				
o  Note that RGB requires higher color comparison tolerances.				
				
The YCbCr method deemphasizes the brightness of the pixel and concentrates on its hue.				
				
The RGB algorithm assesses the similarity of colors using the differences of the RGB components of the pixel in the picture (rgb1) - and the reference pixel mouse-clicked (rgb2): 				
    (r1 - r2)^2 + (g1 - g2)^2 + (b1 - b2)^2 < tolerance^2                 (here '^' is 'squared').				
				
"In the YCbCr algorithm, RGB values are converted to YCbCr (Y is the luminance or brightness and Cb & Cr are color components) and the similarity of colos is assessed by: "				
    (Cb1 - Cb2)^2 + (Cr1 - Cr2)^2 + (Y1 - Y2)^2 / 9 < tolerance^2				
				
"o  ""Print"" - appends a record to 'Coverage.txt' having the format:"				
	"<filename>, result, tolerance, <'RGB' or 'YCbCr'>, RGB_Include[1], RGB_Ignore[1], ... RGB_Include[10], RGB_Ignore[10]"			
"o  ""Avg"" - brings up a message box that displays the average R-G-B components for the image pixels characterized by the non-zero selections 1-10 and the weighted total averages for the R-G-B components of the non-zero selections - and appends the records to 'avg.txt' i.e.:"				
	Sel-1	R:  49	G:  45	B:  36 
	Sel-2	R:  12	G:  11	B:   9 
	. . .			
	Total	R:  49	G:  45	B:  35 
	-------------------------------			
The averaging weights are the percentage of pixels characterized by each non-zero selection.				
