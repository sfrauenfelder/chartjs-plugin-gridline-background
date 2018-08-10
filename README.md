# chartjs-plugin-gridline-background

Plugin for <a href="http://www.chartjs.org/">Chart.js</a> to display colored backgrounds per gridline.

This plugin fills the background of each gridline with configurable colors. Actually, it fills each space _between_ two gridlines.
The gridlines already had configurable foreground colors, and this plugin completes that function with background colors.

<img src="https://rawgit.com/sfrauenfelder/chartjs-plugin-gridline-background/master/demo-picture-all.png" style="width:200px;">

<strong>Tested with</strong> Chart.js 2.7.2, and only with linear, time and category axes. Might work with logarithmic. Expected to fail with other type axes.
<h2>Installation</h2>
Download and save in your project. I don't have a minified version, and it's just one file.
Include into your html, after Chart.js.

<h2>Configuration</h2>
The plugin has two settings, which should be given under the gridLines, in turn under each scale, just like the gridline foreground color. See <a href="http://www.chartjs.org/docs/latest/axes/styling.html#grid-line-configuration">here</a>.
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
<td>The color of the space between this grid line and the next. More details below the table.
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
Detailed explanation of settings:
<table>
   <thead>
      <tr>
         <th>
            backgroundColor
         </th>
         <th colspan=2>
            backgroundColorRepeat
         </th>
      </tr>
     <tr>
      <th></th>
      <th>false</th>
      <th>true</th>
      </tr>
   </thead>
   <tbody>
      <tr>
         <td>
            &lt;not set&gt;
         </td>
         <td colspan=2>
            By default, i.e. if you specify no settings, the plugin will not render anything visible.
         </td>
      </tr>
      <tr>
         <td>
            Single color (string)
         </td>
         <td colspan=2>
            All gridline backgrounds for that axis will be colored with that color. The backgroundColorRepeat has no effect in this case.
         </td>
      </tr>
      <tr>
         <td>
            List of colors (array)
         </td>
         <td>
            The first color applies to the first grid line background, the second to the second grid line background and so on. If there are not enough colors, remaining backgrounds will be left empty.
         </td>
         <td>
            The first color applies to the first grid line background, the second to the second grid line background and so on, until there are no more colors; then we repeat the colors from the first.
         </td>
      </tr>
   </tbody>
</table>

<strong>Note:</strong> For y axes, you have to specify colors from top to bottom, because that's the order in which gridlines are drawn. That's how it works for the gridline foreground colors, and I have followed that for the background colors.
<strong>Note:</strong> If you use opaque (not transparent) colors, only the last drawn colors will be visible, as they are drawn over any previous colors, which are then hidden.
<h2>Example</h2>
The following example would give you alternating grey and white background for an x-axis:

<pre>
options: {
   scales: {
      xAxes: [{
         gridLines: {
            backgroundColor: [ 'lightgrey', 'white' ],
            backgroundColorRepeat: true
         }
      }]
   }
}
</pre>

