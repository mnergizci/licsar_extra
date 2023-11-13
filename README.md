# licsar_extra
Tools for advanced processing of LiCSAR data (starting from geotiffs).
Primarily for unwrapping interferograms (integrated to [LiCSBAS](https://github.com/comet-licsar/licsbas)).

You may install this set of tools e.g. using pip by:  
`
pip install git+https://github.com/comet-licsar/licsar_extra.git
`

Then, to test it, try e.g.:  
```
from licsar_extra import lics_unwrap
help(lics_unwrap.process_ifg_pair)
```

## lics_unwrap.py
Currently, this is the only 'licsar_extra' library, improving the phase unwrapping, as was (partly) described in [IGARSS 2022](https://ieeexplore.ieee.org/document/9884337).
As additional prerequisite, you should install [SNAPHU](http://web.stanford.edu/group/radar/softwareandlinks/sw/snaphu/).

Then, having at least geotiffs of the wrapped interferogram and coherence, you can unwrap e.g. using:
```
phatif = '20xxxxxx_20xxxxxx.unfiltered_pha.geo.tif'
cohtif = '20xxxxxx_20xxxxxx.coh.geo.tif'
outunw = '20xxxxxx_20xxxxxx.unw.geo.tif'
unwcube = lics_unwrap.process_ifg_pair(phatif, cohtif,
        ml = 1, fillby = 'nearest', thres = 0.35, 
        lowpass = False, goldstein = True, specmag = True,
        outtif = outunw, cascade = True) # try cascade True/False, it has strong effect
```
