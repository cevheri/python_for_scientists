# Plotting with matplotlib

Matplotlib is a standard plotting library in Python. That is, people use it all the time to make 2D or 3D informational graphics. This lecture will not be a through guide to matplotlib, because that would take far too long. Instead, this introduction will show you how to make four major types of plots that you (as a scientist/engineer) will want to know how to make. The plots are easy to make and easy to customize.

Matplotlib allows for a dizzying amount of customization, so you can create anything from quick-and-easy plots to publication-quality plots.

![I make a lot of plots](../../resources/simpsons_make_graphs.jpg)

## Installing matplotlib

Like most of the libraries used in our "special topics" lectures, matplotlib does not come standard with Python and will have to be installed. Please check the official [SciPy Stack Install Guide](http://www.scipy.org/install.html). For Linux and Mac, the installation is merely a single line of `apt-get`. For Windows, pre-built installers are provided.

#### Anaconda

Consider installing [Anaconda](http://docs.continuum.io/anaconda/install.html) instead. Anaconda is Python packaged with hundreds of tools and libraries that you will want (This includes matplotlib and everything else we will use in this course.)

## Outline

 * [Scatter Plots](https://github.com/john-science/python_for_scientists/blob/master/classes/12_matplotlib/lecture_12.md#scatter-plots)
 * [Line Plots](https://github.com/john-science/python_for_scientists/blob/master/classes/12_matplotlib/lecture_12.md#line-plots)
 * [Bar Charts](https://github.com/john-science/python_for_scientists/blob/master/classes/12_matplotlib/lecture_12.md#bar-charts)
 * [Histograms](https://github.com/john-science/python_for_scientists/blob/master/classes/12_matplotlib/lecture_12.md#histograms)
 * [Multiple Plots](https://github.com/john-science/python_for_scientists/blob/master/classes/12_matplotlib/lecture_12.md#multiple-plots)
 * [Error Bars](https://github.com/john-science/python_for_scientists/blob/master/classes/12_matplotlib/lecture_12.md#error-bars)
 * [Common Customizations](https://github.com/john-science/python_for_scientists/blob/master/classes/12_matplotlib/lecture_12.md#common-customizations)

## Scatter Plots

First, let's generate a few random numpy arrays:

```python
import numpy as np

N = 100
x = np.random.rand(N)
y = np.random.rand(N)
```

Now, we will use those as X and Y values on a scatter plot:

```python
import matplotlib.pyplot as plt
plt.scatter(x, y)
plt.show()
```

![Simple Scatter Plot](../../resources/scatter1.png)

That's it! Once you have the data, it's just three lines to create a scatter plot!

#### Jupyter Notebooks

If you are using Jupyter Notebooks, you will want to run this command at the top of your notebook:

```python
%matplotlib inline
```

This is *not* Python code, but a Jupyter-specific command to allow your plots to show up inside your notebooks, and not as pop-up windows, or saved as external files. It is super handy and makes your notebooks a lot more sharable and useful.

#### Customizations

Those three lines are great. But you're going to want the power to control how that plot looks. So for each type of plot in this lecture we will show some customization options.

#### Color

We can change the color of the dots in several ways:

```python
# all the same
plt.scatter(x, y, c='red')

# each different
plt.scatter(x, y, c=np.random.rand(N))
```

We can use single letters ('r', 'g', 'b', ...), special words ('red', 'green' 'blue', 'none'), or even numbers from 0.0 to 1.0 to represent colors. And we can provide a single color, or a list of them (one for each point). For more information on color options in matplotlib check the [documentation](http://matplotlib.org/api/colors_api.html) or [these examples](http://matplotlib.org/examples/color/named_colors.html).

#### Size

You can also set the exact size of all the dots on your plot, in pixels, using the `s` option. The size is actually the area, so `s = pi * r * r`, if you want to calculate your radius in pixels you'll have to do a little math. Usually, I just try a couple values and pick the one I like.

Much like color, we can provide one size for all data points, or one size for each data point:

```python
# all the same
plt.scatter(x, y, s=100)

# each different
plt.scatter(x, y, s=100 * np.random.rand(N))
```

#### Alpha

Perhaps you want your dots to be partially transparent, to help see overlapping dots:

```python
# all the same
plt.scatter(x, y, alpha=0.5)
```

Alpha goes from 0.0 (invisible) to 1.0 (not transparent at all).

#### Edge Colors

If you don't want your dot shapes to have those black edges, you can do:

```python
# all the same
plt.scatter(x, y, edgecolors='none')
```

Of course, if you want, you can change the color of your edges using the same terms you used to change the color of the dots:

```python
# all the same
plt.scatter(x, y, edgecolors='b')

# each different
plt.scatter(x, y, edgecolors=np.random.rand(N))
```

#### Full Example

Here is the simple scatter plot example above, using several customizations:

```python
# create random data points
import numpy as np
N = 100
x = np.random.rand(N)
y = np.random.rand(N)

# plot the data
import matplotlib.pyplot as plt
plt.scatter(x, y, c=x*y, s=1000*np.random.rand(N), alpha=0.5, edgecolor='none')
plt.show()
```

![Customized Scatter Plot](../../resources/scatter2.png)

## Line Plots

You can use `plot` to take make a line plot out of a series of points:

```python
# mock up some data
import numpy as np
x = np.arange(10)
y = np.cos(x)

# make a line plot
import matplotlib.pyplot as plt
plt.plot(x, y)
plt.show()
```

![Simple Line Plot](../../resources/line_plot_1.png)

#### Line Style

Your line can be a solid line, or several kinds of dashed lines:

```python
# dashed line
plt.plot(x, y, linestyle='--')

# dashed and dotted line
plt.plot(x, y, linestyle='-.')

# solid line
plt.plot(x, y, linestyle='-')

# dotted
plt.plot(x, y, linestyle=':')
```

#### Line Width

You can also set the width of your line (in pixels):

```python
# thin (default) line width
plt.plot(x, y, linewidth=1)

# very thick line
plt.plot(x, y, linewidth=5)
```

#### Line Color

You set line color using the same options you used to set scatter plot color, but now you can only provide one color, not many:

```python
# red line
plt.plot(x, y, c='red')

# blue line
plt.plot(x, y, c='b')

# white line
plt.plot(x, y, c='white')

# green line
plt.plot(x, y, c='g')
```

#### Full Example

And now let's pull it all together. We can make a line plot of chosen color, width, and style:

```python
# mock up some data
import numpy as np
x = np.arange(10)
y = np.cos(x)

# make a line plot
import matplotlib.pyplot as plt
plt.plot(x, y, linestyle='-.', linewidth=10, c='red')
plt.show()
```

![Fancish Line Plot](../../resources/line_plot_2.png)

## Bar Charts

You can use `bar` to create vertical bar chart:

```python
>>> import numpy as np
>>> N = 20
>>> x = np.arange(N)
>>> y = np.random.randint(1, 100, N)
>>> 
>>> from matplotlib import pyplot as plt
>>> plt.bar(x, y)
>>> plt.show()
```

![Simple Vertical Bar Chart](../../resources/bar_plot_simple_1.png)

Or `barh` to create a horizontal bar chart:

```python
>>> plt.barh(x, y)
>>> plt.show()
```

![Simple Horizontal Bar Chart](../../resources/barh_plot_simple_1.png)

#### Color and Alpha

As before, you can use `color` and `alpha` keywords to set the color and transparency of your bars.

#### Align

Use the `align` keyword to orient your bars in relation to the values they represent. You have to options:

```python
# align bars so left edge is on their values (default)
plt.bar(x, y, align='edge')

# align bars so they are centers on their values
plt.bar(x, y, align='center')
```

#### Edgecolor

Use the `edgecolor` keyword to set the outline color of your bars.

```python
# set no outline
plt.barh(x, y, edgecolor='none')

# set outline color to blue
plt.barh(x, y, edgecolor='blue')
```

#### Width

Use `width` to make the bars wider or thinner. You can set the width of them as you want. But if your width is greater than the spacing of your bars, they will overlap.

```python
# bars just barely touch
plt.bar(x, y, width=1.0)

# bars are far apart
plt.bar(x, y, width=0.5)
```

#### Log

Use `log=True` if you want your bar chart to be logarithmic along the Y-axis. The default is `log=False`.

#### Bottom: Stacked Bar Charts

Use `bottom` to shift offset a set of bars up above the X-axis. This will allow you to plot multiple bars in a multiple bar chart:

```python
>>> import numpy as np
>>> x = np.array([1, 2, 3, 4, 5])
>>> y1 = np.array([2, 3, 4, 6, 4])
>>> y2 = np.array([7, 5, 4, 6, 8])
>>> 
>>> from matplotlib import pyplot as plt
>>> plt.bar(x, y1, color='b')
>>> plt.bar(x, y2, color='r', bottom=y1)
>>> plt.show()
```

#### Full Example

Let's put it all together and make a stacked bar chart with custom colors and widths.

```python
import numpy as np
N = 10
x = numpy.arange(N)
y1 = np.random.randint(1, 30, N)
y2 = np.random.randint(1, 10, N)
y3 = np.random.randint(1, 20, N)

from matplotlib import pyplot as plt
plt.bar(x, y1, color='r', edgecolor='none', width=0.9)
plt.bar(x, y2, color='g', edgecolor='none', width=0.9, bottom=y1)
plt.bar(x, y3, color='b', edgecolor='none', width=0.9, bottom=y1+y2)
plt.show()
```

![Stack Bar Chart](../../resources/bar_plot_fancy_1.png)

## Histograms

You can `hist` to create a histogram:

```python
# x is some array of values
plt.hist(x, 10)
```

#### alpha and edgecolor

Use `alpha` and `edgecolor` just like you did for bar charts.

#### facecolor

Use `facecolor` as you would the `color` keyword for bar charts or scatter plots.

#### normed

Use `normed` to normalize your histogram so the vertical scale represents the probability of the data lying in each bin (`normed=1`).

#### Full Example

```python
import numpy as np
from matplotlib import pyplot as plt
mu = 100
sigma = 20
data = mu + sigma * np.random.randn(1000)

plt.hist(data, 20, normed=1, facecolor='r', edgecolor='none')
plt.show()
```

![Normalized Histogram](../../resources/histogram_plot_1.png)

## Multiple Plots

For the most part, putting multiple datasets on the same plot is super easy; you just add more plots to `matplotlib.pyplot` before you `pyplot.show()`.

```python
# x = some X-values
# y1 = some Y-values
# y2 = some other Y-values
```

For scatter plots:

```python
from matplotlib import pyplot as plt
plt.scatter(x, y1)
plt.scatter(x, y2)
plt.show()
```
    
For line plots, the same thing:

```python
from matplotlib import pyplot as plt
plt.plot(x, y1)
plt.plot(x, y2)
plt.show()
```

And this even gives us a nice option, we can overlay a scatter plot with a line plot, to show the relationship between our measurements:

```python
from matplotlib import pyplot as plt
plt.scatter(x, y1)
plt.plot(x, y1)
plt.show()
```

![Line-and-Scatter Plot](../../resources/line_and_scatter_plot_1.png)

For bar charts, it is a little different; we need to place the bars side-by-side. This means we have to do a little math about the width of the bars:

```python
# define data
import numpy as np

N = 10
x = np.arange(N)
y1 = np.random.randint(5, 50, N)
y2 = np.random.randint(5, 25, N)

# create plot
import matplotlib.pyplot as plt

width = 0.4
plt.bar(x, y1, width, color='b')
plt.bar(x + width, y2, width, color='r')
plt.show()
```

![Multi-Bar Plot](../../resources/multibar_plot_1.png)

## Subplots - One Image

Frequently, in a real-world analysis, we will want to show more than one plot at a time. We do this in matplotlib by making subplots on our image. There are two ways to accomplish this.

First way, `plt.subplots(ncols=N1, nrows=N2)`:

```python
# create random data points
import numpy as np
N = 100
x = np.random.rand(N)
y = np.random.rand(N)

# plot the data on two side-by-side subplots
import matplotlib.pyplot as plt
fig, (col1, col2) = plt.subplots(ncols=2)
col1.plot(x, y)
col2.scatter(y, x)
plt.show()
```

![Simple 2-Column plot](../../resources/simple_2_column_plot_1.png)

So, what did we do here? First, we mocked up some random data. Then we used `pyplot.subplots` to define that our image would have two columns of plots. Then we just added two plots to the image: one line and one scatter. And they are put in sequential order; the first plot added is the first column and the second plot goes into the second column.

Second way, `plt.subplot(NROWS, NCOLS, NPLOT)`:

```python
plt.subplot(1, 2, 1)
plt.plot(x, y)
plt.subplot(1, 2, 2)
plt.scatter(y, x)
plt.show()
```

This will produce the exact same 2-column plot as before. The only difference is that we used multiple `subplot` statements, rather than a single `subplots` statement.

## Error Bars

Use `errorbar` to create a `plot`-like line plot, with error bars:

```python
# mock up some data
import numpy as np
x = np.arange(10)
y = np.cos(x)

# make a line plot
import matplotlib.pyplot as plt
plt.errorbar(x, y, xerr=0.2, yerr=0.4)
plt.show()
```

Or, if you want error bars on your bar charts, use `xerr` and `yerr` parameters there as well:

```python
plt.bar(x, y, xerr=0.2, yerr=0.4)
```

#### Full Example

Here is a complete plot of both types of ways to create plots with error bars. Also included, you'll notice, is a way to put error bars on a scatter plot, by setting `linestyle=none` on the `errorbar` plot:

```python
# mock up some crazy data
import numpy as np
x = np.arange(0.0, pi, pi/16)
y1 = np.cosh(x)
y2 = np.cos(x)

# create scatter plot with error bars
from matplotlib import pyplot as plt
fig, (col1, col2) = plt.subplots(ncols=2)
col1.errorbar(x, y1, yerr=np.arange(0.2, 1.2, 1.0/16), linestyle='none', ecolor='black')
col1.scatter(x, y1, alpha=0.75, c=np.arange(0.0, 1.0, 1.0/16.0), s=np.arange(0.0, 600, 600.0/16), edgecolor='none')

# create bar chart with error bars
col2.bar(x, y2, width=(pi/16)*0.8, xerr=0.1, yerr=0.25, color='red', edgecolor='none', ecolor='black')
plt.show()
```

![Subplots with Errorbars](../../resources/subplots_with_error_bars.png)

## Common Customizations

The various plot types above are extremely useful for displaying all kinds of scientific data. But plots tend to have more than just raw data information. They can have legends, titles, axis labels, and more. So let's take a quick look at how you can add some of these common features to your plots.

Use `.title()` to add a title to your plot:

```python
plt.scatter(x, y)
plt.title('Mortality rate of base jumpers over time')
plt.show()
```

Use `.xlabel()` and `.ylabel()` to add labels to the X and Y-axis independently:

```python
plt.scatter(x, y)
plt.yaxis('Deaths')
plt.xaxis('year')
plt.show()
```

Use `xlim(XMIN, XMAX)` and `ymin(YMIN, YMAX)` to manually set the range of the X or Y-axis:

```python
plt.scatter(x, y)
plt.xlim(1985, 2015)
plt.ylim(1, 100)
plt.show()
```

Use `.grid()` to add a little gridded pattern to the background of the plot:

```python
plt.scatter(x, y)
plt.grid()
plt.show()
```

Use `.legend()` to add a legend to your plot. To do this, make sure and add a `label=XXX` attribute to each of your data plots:

```python
plt.scatter(x, y1, label='Deaths from Equipment Failure')
plt.scatter(x, y1, label='Total Deaths')
plt.legend()
plt.show()
```

Use `.savefig(FILE_PATH)` to save your plot to a file:

```python
plt.scatter(x, y)
plt.savefig('/path/to/my_file.png')
```

#### Full Example

Here is a heavily customized plot, using all of the above options:

```python
# data taking from Google Ngram Viewer
import numpy as np
years = np.arange(1920, 2011, 5)
machine_age = np.array([5.0, 10, 110, 190, 130, 100, 73, 55, 43, 69, 35, 30, 25, 20, 21, 18, 20, 17, 10])
machine_age /= 1.0e6
space_age = np.array([0.0, 0, 0, 0, 0, 0, 0, 5, 52, 38, 43, 35, 30, 33, 28, 20, 19, 16, 8])
space_age /= 1.0e6
information_age = np.array([0.0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 8, 41, 43, 79, 131, 121, 98])
information_age /= 1.0e6

# making customized triple-plot
from matplotlib import pyplot as plt
plt.plot(years, machine_age, c='green', linewidth=3, label='Machine Age')
plt.plot(years, space_age, c='red', linewidth=3, label='Space Age')
plt.plot(years, information_age, c='blue', linewidth=3, label='Information Age')
plt.grid()
plt.title('Relative Occurance of Terms in Books Over Time')
plt.xlabel('year')
plt.ylabel('Word Occurence (% of published works)')
plt.xlim(1920, 2008)
plt.ylim(0, 0.0002)
plt.legend()
plt.savefig('information_age.png')
```

![Google Ngram Plot](../../resources/information_age.png)


## Style Sheets

Matplotlib gives you a *lot* of power to customize plots. But the more custom you want it to look, the more time it takes. Wouldn't it be great if there were some way to define all your common customizations at once, and save them off for later? Great idea, we'll call it a "style sheet".

For instance, if you want your plots to look like they were made in the R programming language with `ggplot`, you just need to add one line to your file:

```python
plt.style.use('ggplot')
```

In fact, MatPlotLib has a lot of default styles built in. See [here](https://matplotlib.org/examples/style_sheets/style_sheets_reference.html) for more examples.

And you can easily build your own style sheet in a config-file format, which you can find more about [here](https://matplotlib.org/users/style_sheets.html).


## The Warning - 1000 ways to skin a cat

There are a *lot* of different ways to do basically everything in matplotlib. It will be easiest to learn how to use matplotlib if you figure out how to do things *one* way and just ignore all the other options. I know, I know, that doesn't sound ideal. But most of us will make plots by looking at examples online. And if you are constantly seeing different ways to do the same things it will take much longer for you to learn how to do things on your own.

Are the methods presented in this lecture the only way to do things? No. But pick one way to do things in matplotlib, and find a reference that is consistent. That's the important thing.


## Final Note - Backends, A Common Problem

Sometimes matplotlib will just refuse to work at all. It turns out, sometimes, you need to tell matplotlib about where you are or what you are doing. The relevant questions are things like:

 * Am I running matplotlib from the commandline?
 * Am I running matplotlib from an automated script?
 * Am I looking at the plots (`.show()`), or saving them to files (`.savefig()`)?
 * Am I creating PNG outputfiles, or PS, or what?

All you need to do is set the "backend" for matplotlib, so it knows what you are doing. It's just two lines. Hopefully you don't run into this problem, but if you do, look at the full explanation and guide [here](http://matplotlib.org/faq/usage_faq.html#what-is-a-backend).

## Matplotlib through Jupyter Notebooks

This lecture is also available as a series of Jupyter (iPython) notebooks. Which you can see rendered in all their beauty here. They cover somewhat more information than what is above, with plots and all included right there.

1. [Line Plots](1_line_plots.ipynb)
2. [Scatter Plots](2_points_and_errorbars.ipynb) - and Error Bars
3. [Histograms](3_histograms.ipynb)
4. [Multi-Panel Figures](4_multipanel_figures.ipynb)
5. [Stylizing Plots](5_stylizing_plots.ipynb)
6. [Interactive Plots](interactive_plots.py) - example Python script
7. [Interactive Plots](interactive_plots2.py) - example Python script (OOP)

You can even download these Notebooks and run them yourself! Have fun with them, play around with the plots. It's the best way to learn.


## Problem Set

 * [Example Matplot Problems](problem_set_1_matplotlib.md)

## Further Reading

Matplotlib is a powerful tool. But there are so many plots and customization options that memorizing them all would be a huge waste of time. So I cheat. [Here](http://matplotlib.org/gallery.html) is the cheat sheet: a wonderful collection of matplotlib examples.

 * [matplotlib gallery](http://matplotlib.org/gallery.html)
 * [matplotlib color docs](http://matplotlib.org/api/colors_api.html)
 * [matplotlib color examples](http://matplotlib.org/examples/color/named_colors.html)
 * [Google Ngram Viewer](https://books.google.com/ngrams/)
 * [matplotlib backends](http://matplotlib.org/faq/usage_faq.html#what-is-a-backend)

[Back to Syllabus](../../README.md)
