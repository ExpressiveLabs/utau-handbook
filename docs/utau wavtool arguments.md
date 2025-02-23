*<outfile> - synthesized output, stored in the cache folder of a UST, then used/resynthesized for a final render
<infile> - input sample used for synthesis
*offset - starting point of an alias for a sample, changeable via STP in note property
length - length of synthesized output

p = position in time
v = volume

p1, v1 = "current overlap point 1" p = starting silence when p2p3 is used, p = end of current overlap when p1p4 is used

p2, v2 = "current overlap point 2" p = end of current overlap when p2p3 is used, unused when p1p4 is used

p3, v3 = "next overlap point 1" p = start of next overlap when p2p3 is used, unused when p1p4 is used

p4, v4 = "next overlap point 2" p = ending silence when p2p3 is used, p = start of next overlap when p1p4 is used

p5, v5 = "middle point," unused by default

ovr = i'm not sure, seems to abbreviate overlap