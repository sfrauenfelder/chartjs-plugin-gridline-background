# chartjs-plugin-gridline-background

Plugin for <a href="http://www.chartjs.org/">Chart.js</a> to display colored backgrounds per gridline.

This plugin fills the background of each gridline with configurable colors. Actually, it fills each space _between_ two gridlines.
The gridlines already had configurable foreground colors, and this plugin completes that function.

<img src="https://rawgit.com/sfrauenfelder/chartjs-plugin-gridline-background/master/demo-picture.png" style="width:200px;">

Tested with Chart.js 2.7.2, and only with linear, time and category axes. Might work with logarithmic. Expected to fail with other type axes.
<h2>Installation</h2>
Download and save in your project. I don't have a minified version, and it's just one file.
Include into your html, after Chart.js.

<h2>Configuration</h2>
The plugin has two settings, which should be given under the gridLines (under each scale, just like the gridline foreground color):
<table>
<thead>
<tr>
<th>Name</th>
<th>Type</th>
<th>Default</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>backgroundColor</code></td>
<td><code>Color/Color[]</code></td>
<td><code>'rgba(0, 0, 0, 0.0)'</code></td>
<td>The color of the space between this grid line and the next.
   If specified as an array, the first color applies to the first grid line, the second to the second grid line and so on.
   As a string (single color), all gridline background will be colored with this color.
   </td>
</tr>
<tr>
<td><code>backgroundColorRepeat</code></td>
<td><code>true/false</code></td>
<td><code>false</code></td>
<td>Whether the colors should be repeated. So for example you can specify two colors, which will then be repeated for all gridlines. 
   </td>
</tr>
 </tbody>
</table>
By default, the plugin will not render anything visible.

<strong>Note:</strong> for y axes, you have to specify colors from top to bottom, because that's the order in which gridlines are drawn. That's how it works for the gridline foreground colors, and I have followed that for the background colors.

<h2>Example</h2>
The following example would give you alternating grey and white background for an x-axis:

<pre>
options: {
   scales: {
      xAxes: [{
         gridLines: {
            backgroundColor: [ 'grey', 'white' ],
            backgroundColorRepeat: true
         }
      }]
   }
}
</pre>


The option backgroundColorRepeat: true makes the plugin repeat the sepcified background colors. If set to false in this example, it would only color the first two gridline backgrounds.

