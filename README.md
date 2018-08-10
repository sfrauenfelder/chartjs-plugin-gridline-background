# chartjs-plugin-gridline-background
<div style="display: inline-block;width: 50%;float: left;">
Plugin for <a href="http://www.chartjs.org/">Chart.js</a> to display colored backgrounds per gridline.

This plugin fills the background of each gridline with configurable colors. Actually, it fills each space _between_ two gridlines.
The gridlines already had configurable foreground colors, and this plugin completes that function.

Tested with Chart.js 2.7.2, and only with linear, time and category axes. Might work with logarithmic. Expected to fail with other type axes.
</div>
<div style="display: inline-block;width: 50%;float: left;">
<img src="https://rawgit.com/sfrauenfelder/chartjs-plugin-gridline-background/master/demo-picture.png" style="width:200px;">
</div>
<h2>Installation</h2>
Download and save in your project. I don't have a minified version, and it's just one file.
Include into your html, after Chart.js.

<h2>Configuration</h2>
By default, the plugin will not render anything visible.

Regular intended configuration is as a list of backgroundColors with the gridLines options, similar to specifying the gridline foreground color. You can also make the background colors repeat, via a simple boolean option.

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
