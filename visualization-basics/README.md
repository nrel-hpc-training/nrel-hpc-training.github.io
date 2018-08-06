# Introduction to visualization

You have data. It might have come from an experiment or a simulation. It could fill 1kB or 1PB of memory. And you may be able to understand it in its raw form. But if it's not that simple, or you need to communicate it to another person, I beg you to consider visualization.


## The short version

Is your data:

* *Bivariate, straightfoward in format, or under 1MB in size?* - Install and open Microsoft Excel, import your data, generate plots.
* *Already in an integrated package like R, Matlab, or Mathematica?* - Use those built-in tools for plotting and analysis.
* *Multivariate, spatial, or under 1GB in size?* - Install and open ParaView, load or import your data, hit the "Apply" button in the "Properties" tab, then possibly select a different "Representation" or begin applying filters.
* *Highly domain-specific or very large?* - Ask a fellow researcher or a member of the DAV (Data, Analysis, Visualization) team about your options.


## Let's think about this for a moment


#### Which tools are most appropriate?
Very often, your data format limits your choice of visualization tools. Converting the data into a more general format can open up more possibilities, but that isn't always possible. Here are some suggestions for data visualization software for various problem domains or data types.

* Molecular dynamics - Look at VMD or ParaView
* Computational fluid dynamics - Ensight or ParaView
* High-dimensional data - xxx
* Grid or Power flow - xxx
* Gene expression or sequencing data - xxx
* Finite-element methods - xxx

#### Where is your data?

If your data fits on your laptop or desktop, chances are you can create visualizations there as well. Links to software on this page will take you to their download page, which typically also have installation instructions.

If your data was the result of a supercomputer calculation, and is much too large for desktop workstations to handle, you should use one of Peregrine's new visualization nodes: `dav4` to `dav6`. These machines provide modules for several useful and powerful data visualization packages, such as: Aviso, ParaView, and VisIt. First, install [FastX](https://www.nrel.gov/hpc/software-fastx.html) and connect to one of the DAV nodes (`dav4.hpc.nrel.gov` to `dav6.hpc.nrel.gov`). Then enable the software with these two commands:

```
module use /nopt/nrel/apps/modules/default/modulefiles
module load aviso paraview visit
```

Your data should already be accessible from the `/scratch` or `/projects` file systems, so run one of the above programs and start exploring.

#### How will your visualization be delivered?

There is a wealth of software and methods to match the wide variety of visualization types. Consider the details below...

* **2D Plots** - These are vector graphics which will ultimately go into a paper or poster. *Save as EPS or PDF, not JPG!*

  Spreadsheet software includes *Excel* on Windows or OSX, *Numbers* on OSX, and [LibreOffice](https://www.libreoffice.org/download/download/)

  *Grapher* on OSX (use Equation->New Point Set and then Import...)

  *gnuplot* on Linux (try `sudo yum install gnuplot`)

  *Graphvis* renders graphs and networks to raster or vector formats

* **Poster** - You're laying out a short, coherent, and visual summary of your research. *Save as SVG or PDF*

  [Inkscape](https://inkscape.org/en/download/) for OSX, Windows, or Linux

  *Pages* on OSX

  [LibreOffice](https://www.libreoffice.org/download/download/) has a "Draw" module

* **Rendering** - For professional-looking 2D raster images with accurate shading and depth cues. *Save as PNG, not JPG*

  [Blender](https://www.blender.org/download/) is an incredibly-deep and capable 3D modeling, rendering, and animation program, but has a steep learning curve. Nevertheless, it is very popular, and you may find co-workers who are familiar with it.

  [ParaView with OSPRay](https://www.paraview.org/download/) (versions 5.4 and newer) - At the bottom of the "Properties" tab are options for rendering with Intel's CPU-accelerated OSPRay ray-tracing library. Set up your visualization first, and then turn it on; make sure to use shadows and ambient passes for best quality.

  Consider rendering your 2D images at FHD (1920x1080) or larger for two reasons: it's easy to incorporate it into videos, and you likely won't need to re-render the image years later in higher resolution.

* **Video** - More engaging than a still image, for supplementary media. *Save as MP4 with X.264 encoding for best compatibility.*

  [Handbrake](https://handbrake.fr/downloads.php) on OSX, Windows, or Ubuntu is a great choice.

  [ffmpeg](https://www.ffmpeg.org/) on Linux. You can encode a series of png files to a compressed video that will play on all OSs with:

  `ffmpeg -f image2 -i image-%04d.png -c:v libx264 -crf 20 -framerate 30 -profile:v baseline -level 3.0 -pix_fmt yuv420p -f mp4 output.mp4`

  See more ffmpeg options [here](https://trac.ffmpeg.org/wiki/Encode/H.264).

* **Interactive** - More than just a static plot, you can let the user interact with your data in real-time

  [Aurelia](http://aurelia.io) or [Plotly](http://plot.ly) for JavaScript visualization for the web

  [R Studio](https://www.rstudio.com/products/rstudio/download/) to present tabular or statistical data along with code

  [Jupyter Notebook](http://jupyter.org/install) is a combined programming, visualization, and publishing environment for data scientists

* **3D** - 3D printing, WebGL, point cloud, etc. *Maximum portability with PLY, OBJ, or X3D formats*

  [Meshlab](http://www.meshlab.net/#download) can help you create and manipulate 3D meshes of triangles or quads.

  NREL has a 3D printing lab, and [Shapeways](http://shapeways.com) or [Sculpteo](http://www.sculpteo.com/en) are two online 3D printing service providers.

#### Do you have to make a lot of these?

You'll always start making one-off plots, but if you wind up creating similar plots more that a few times, especially for videos, consider scripting the operation. Many programs offer scripting support, including ParaView, Blender, gnuplot, Meshlab, and VMD.

To begin scripting with ParaView, open up a fresh session, then select "Tools"->"Start Trace" and then "OK". Perform all of the operations you need to generate your plots (this means loading the data, setting up the filter chain, up to and including "File"->"Save Screenshot..."). Once you're done, select "Tools"->"Stop Trace" and save the resulting Python file (let's call it `pvrender.py`). You can then re-run the operations later by running:

```
pvbatch --use-offscreen-rendering pvrender.py
```
## For More Information

Please visit the [NREL HPC Website](https://nrel-dev.nrel.gov/hpc/about-hpc.html) to see available Office Hours and contact information.  During our office hours, HPC system users at NREL may drop in to meet with staff to get started, ask questions, or resolve any issues. If these hours don’t work for you, you may arrange a different time with the contact. 
