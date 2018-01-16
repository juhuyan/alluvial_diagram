# alluvial_diagram
A python script for generating "alluvial" styled bipartite diagrams, using matplotlib and numpy

## Getting Started

Copy alluvial.py to your working directory, and follow the syntax in the examples below.
See "Advanced use" for a mild parameter documentation.

### Prerequisites

matplotlib and numpy

### Installing

Copy alluvial.py to your working directory.

#### Example 1:
<pre><code>
import alluvial
import matplotlib.pyplot as plt
import numpy as np

input_data = {'a': {'aa': 0.3, 'cc': 0.7,},
              'b': {'aa': 2, 'bb': 0.5,},
              'c': {'aa': 0.5, 'cc': 1.5,}}
ax = alluvial.plot(input_data)
fig = ax.get_figure()
fig.set_size_inches(5,5)
plt.show()
</code></pre>
![](/image_examples/Example1.png)

#### Example 2:
<pre><code>
import alluvial
import matplotlib.pyplot as plt
import matplotlib.cm
import numpy as np

# Generating the input_data:
def rand(mm):
    return int((mm**2)*np.random.rand()//mm)
mm = 5
input_data = {
  chr(rand(mm*4)+65): {chr(rand(mm)+97): 4*rand(mm) for _ in range(mm)} for _ in range(mm*4)}

# Plotting:
cmap = matplotlib.cm.get_cmap('gist_rainbow')
ax = alluvial.plot(
  input_data,  alpha=0.6, color_side=1, rand_seed=1, show_width=True, figsize=(5,6), cmap=cmap)
fig = ax.get_figure()
plt.show()
</code></pre>
![](/image_examples/Example2.png)

### Advanced use
* Additional input format - a list of tuples of structure:
  * input_data = [('a_item0', 'b_item0'), ('a_item0', 'b_item1') , ('a_item1', 'b_item0')]
* Parameters and default values:
  * alpha = 0.4 - defines facecolor alpha for all veins
  * color_side = 0 - vein colors determined by left side items (0) or right side items (1)
  * rand_seed = 0 - a seed for the random color generator
  * show_width = False - if True, displays vein widths beside item labels
  * x_range=(0, 1) - changes the horizontal plot coordinates
  * res=20 - determines the number of points constituting the alluvial vein spline
  * h_gap_frac=0.03 - changes the horizontal gap between the letters, blocks and veins
  * v_gap_frac=0.03 - changes the vertical gap between veins
  * colors - a list of numbers between 0 and 1 defining colors for the color map.
  * a_sort, b_sort - lists defining plot order of items (both are None by default)


## License

This project is licensed under the Apache 2.0 License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Inspired by the alluvial diagram example given in the [rawgraphs website](http://rawgraphs.io/gallery_project/visualizations-for-issue-mapping-book/).


