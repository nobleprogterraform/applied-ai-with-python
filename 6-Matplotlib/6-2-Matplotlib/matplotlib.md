### Summary of Matplotlib Concepts Lecture

#### Introduction
In this first lecture on Matplotlib, we explore how to use this powerful plotting library in Python. The session focuses on foundational concepts, installation, and basic plotting techniques, utilizing a Jupyter notebook environment.

#### Setting Up
To start using Matplotlib, first ensure it is installed. You can do this via the command line with either:
- `pip install matplotlib` (for standard Python installations)
- `conda install matplotlib` (for Anaconda users)

In a Jupyter notebook, begin by importing Matplotlib with the following command:
```python
import matplotlib.pyplot as plt
```
To enable inline plotting (displaying plots directly within the notebook), use:
```python
%matplotlib inline
```

#### Basic Plotting
We begin with a simple example using NumPy to create linearly spaced data. Import NumPy and generate data as follows:
```python
import numpy as np
x = np.linspace(0, 5, 11)  # 11 points from 0 to 5
y = x ** 2  # Squaring each element
```

##### Functional Method
Matplotlib allows two primary methods for plotting: functional and object-oriented. We first demonstrate the functional approach:
```python
plt.plot(x, y)
```
In a non-Jupyter environment, you would conclude your plotting commands with:
```python
plt.show()
```
In Jupyter, simply running the plot command displays the output directly.

You can enhance your plots by adding labels and titles:
```python
plt.xlabel('X Label')
plt.ylabel('Y Label')
plt.title('Title of the Plot')
```

#### Creating Subplots
To create multiple plots in a single figure, use the `plt.subplot()` function:
```python
plt.subplot(1, 2, 1)  # 1 row, 2 columns, 1st subplot
plt.plot(x, y, 'r')  # Plot in red

plt.subplot(1, 2, 2)  # 1 row, 2 columns, 2nd subplot
plt.plot(y, x, 'b')  # Plot in blue
```

#### Object-Oriented Approach
Transitioning to the object-oriented method, we create a figure object for more control:
```python
fig = plt.figure()  # Create a figure object
ax = fig.add_axes([left, bottom, width, height])  # Define axes in normalized coordinates
```
Here, `left`, `bottom`, `width`, and `height` are parameters between 0 and 1, indicating the position and size of the axes.

Plotting on the axes looks similar but utilizes the axes object:
```python
ax.plot(x, y)
```
You can still set labels and titles, but the method calls change slightly:
```python
ax.set_xlabel('X Label')
ax.set_ylabel('Y Label')
ax.set_title('Title of the Plot')
```

#### Multiple Axes
Creating multiple axes on one figure is straightforward. Define each axes and plot accordingly:
```python
ax1 = fig.add_axes([0.1, 0.1, 0.8, 0.8])  # Main axes
ax2 = fig.add_axes([0.2, 0.5, 0.4, 0.3])  # Inset axes
```
You can then plot on each axes separately:
```python
ax1.plot(x, y)
ax2.plot(y, x)
```
Setting titles for clarity is also possible:
```python
ax1.set_title('Larger Plot')
ax2.set_title('Smaller Plot')
```

#### Conclusion
The lecture emphasized the importance of understanding both the functional and object-oriented approaches to Matplotlib. While the functional method is simpler for quick plots, the object-oriented method offers more flexibility and control for complex visualizations. 

For further practice, students are encouraged to explore the provided Jupyter notebook, which includes additional notes and examples. Understanding the creation of figure objects, axes, and how to manipulate them lays the groundwork for more advanced plotting techniques in future lectures.

### Next Steps
In the next lecture, we will continue building on these concepts and explore more advanced features and techniques within Matplotlib. Thank you for participating, and see you next time!


In this lecture on Matplotlib, we delve deeper into object-oriented programming methods for creating visualizations, building upon the functional programming techniques introduced previously. The focus is on utilizing the `subplots` functionality for better figure management.

### Subplots Creation

The instructor starts by demonstrating how to create subplots using the `plt.subplots()` function. This method returns a figure object and an array of axes, allowing for easy management of multiple plots. For example, to create a 1x2 subplot layout, the call would be:

```python
fig, axes = plt.subplots(nrows=1, ncols=2)
```

This creates one row with two columns of plots. The axes can then be accessed as an array, enabling iteration or direct indexing to plot data. The ability to manage multiple axes efficiently is emphasized, illustrating how this approach simplifies plotting compared to manual axes creation.

### Iterating and Indexing Axes

The axes object can be treated like a list, allowing iteration through the axes to plot data or to set titles and labels. For instance:

```python
for current_ax in axes:
    current_ax.plot(x, y)
```

This capability makes it easy to apply the same plotting function across multiple subplots, ensuring consistency in appearance and labeling.

### Managing Layouts

To address potential overlapping of plots, the instructor highlights the utility of `plt.tight_layout()`, which automatically adjusts the spacing of subplots to minimize overlap. This is recommended as a best practice after defining the layout.

### Figure Size and DPI Control

The lecture then transitions to discussing figure size and DPI (dots per inch). The figure size can be defined during figure creation using:

```python
fig = plt.figure(figsize=(width, height))
```

where `width` and `height` are specified in inches. DPI can also be set for high-resolution outputs:

```python
fig = plt.figure(figsize=(8, 2), dpi=100)
```

This allows for fine control over the appearance of the plots in different contexts, such as presentations or publications.

### Saving Figures

To save a figure in various formats (e.g., PNG, JPEG), the `savefig()` method is used:

```python
fig.savefig('my_picture.png', dpi=200)
```

This line saves the current figure with specified resolution, providing flexibility for output formats.

### Adding Titles and Labels

The instructor briefly reviews setting titles and labels for axes. For example, using:

```python
axes[0].set_title('First Plot')
axes[1].set_ylabel('Y Axis Label')
```

This approach allows for clear communication of what each subplot represents, crucial for effective data visualization.

### Adding Legends

Legends are introduced as a means of clarifying multiple plots. The process involves two main steps: first, defining a label during the plot call:

```python
axes[0].plot(x, y, label='Label for Y')
```

and then calling `axes[0].legend()` to display the legend. The placement of the legend can be controlled with parameters, and the instructor advises using `loc=0` for automatic positioning.

### Conclusion and Next Steps

The lecture concludes with a preview of the upcoming topics, including customizing colors, line styles, markers, and ranges for plots, as well as an introduction to Seaborn for enhanced visualization capabilities. The instructor encourages students to ask questions and refer to the provided notebooks for further practice and exploration of Matplotlib features.

Overall, this session builds a strong foundation in object-oriented plotting with Matplotlib, equipping students with the tools to create complex visualizations efficiently.


In Part 3 of the Matplotlib lecture series, we dive into advanced customization options for plots, focusing on colors, line styles, and markers. The session is conducted through a Jupyter notebook, providing hands-on coding examples.

### Setting Colors
We begin by creating a figure and adding axes using:
```python
fig = plt.figure()
axes = fig.add_axes([0, 0, 1, 1])
```
To plot data, the command is straightforward:
```python
axes.plot(x, y)
```
Colors can be customized using the `color` parameter, which accepts basic color strings like "blue" or "orange", as well as RGB hex codes. For example:
```python
axes.plot(x, y, color='orange')  # Basic color
axes.plot(x, y, color='#ff8c00')  # Custom RGB hex code
```
Tools for generating hex codes are recommended for users wanting specific colors.

### Line Width and Style
The line width can be adjusted by specifying the `linewidth` parameter. For instance, to double the default width:
```python
axes.plot(x, y, linewidth=2)
```
The `alpha` parameter allows control over line transparency, with a range from 0 (completely transparent) to 1 (fully opaque):
```python
axes.plot(x, y, linewidth=2, alpha=0.5)
```
For line styles, options include solid, dashed, and dotted lines, represented by strings like `'-'` for solid and `'--'` for dashed:
```python
axes.plot(x, y, linestyle='--')  # Dashed line
```
Abbreviated versions of parameters (`lw` for `linewidth` and `ls` for `linestyle`) can also be used.

### Markers
Markers indicate data points, especially useful when plotting discrete values. They can be customized with:
```python
axes.plot(x, y, marker='o')  # Circle marker
```
Various marker symbols are available, such as `+`, `*`, and other shapes, allowing for extensive customization. The size of markers can be adjusted with the `markersize` parameter:
```python
axes.plot(x, y, marker='o', markersize=10)
```
Further customizations include marker face color, edge width, and edge color:
```python
axes.plot(x, y, marker='o', markerfacecolor='yellow', markeredgewidth=3, markeredgecolor='green')
```

### Controlling Axes and Plot Range
To set the limits of the x-axis and y-axis, we use:
```python
axes.set_xlim([0, 1])  # Set x-axis limits
axes.set_ylim([0, 2])  # Set y-axis limits
```
This allows for zooming in on specific sections of the plot, enhancing clarity and detail.

### Specialized Plot Types
While the focus is on customizing line plots, Matplotlib also supports various specialized plot types such as scatter plots, bar plots, and histograms. These are briefly mentioned with a note that Seaborn, a complementary library, is better suited for statistical visualizations.

### Additional Resources
Participants are encouraged to refer to the Jupyter notebook for detailed examples and links for further reading, including a comprehensive Matplotlib tutorial.

In conclusion, this lecture emphasizes the versatility of Matplotlib for creating customized plots, while also pointing to Seaborn for more advanced statistical visualizations. The session ends with a prompt to explore practical exercises and upcoming lectures.