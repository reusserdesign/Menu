<h1>Menu</h1>
<p>It's tedious to build drop down functionality into navigation menus for every project. Menu is a simple Sass mixin that handles <em>just</em> the drop down functionality for a nested list. Not only does Menu handle a single drop down, it goes to the infinite level. Your sub-sub-sub-sub-sub-sub menu is safe.</p>

<h2>Demo</h2>
<p>Because every thing needs to be demonstrated. <a href="http://www.reusserdesign.com/blog/demo/menu/index.html" target="_blank">View the demo</a></p>

<h2>Browser Support</h2>
<ul>
	<li>Internet Explorer 8+</li>
	<li>Firefox 3.6+</li>
	<li>Chrome 9+</li>
	<li>Safari 4+</li>
</ul>

<h2>How To Use</h2>
<p>In your HTML, create a navigation menu using an unordered list. For example:</p>
<pre>
	&lt;ul&gt;
		&lt;li&gt;&lt;a href="#"&gt;Home&lt;/a&gt;&lt;/li&gt;
		&lt;li&gt;&lt;a href="#"&gt;The Band&lt;/a&gt;
			&lt;ul&gt;
				&lt;li&gt;&lt;a href="#"&gt;Dr. Teeth&lt;/a&gt;&lt;/li&gt;
				&lt;li&gt;&lt;a href="#"&gt;Animal&lt;/a&gt;
					&lt;ul&gt;
						&lt;li&gt;&lt;a href="#"&gt;Biography&lt;/a&gt;&lt;/li&gt;
						&lt;li&gt;&lt;a href="#"&gt;Blog&lt;/a&gt;&lt;/li&gt;
						&lt;li&gt;&lt;a href="#"&gt;Reviews&lt;/a&gt;&lt;/li&gt;
						&lt;li&gt;&lt;a href="#"&gt;Music&lt;/a&gt;
							&lt;ul&gt;
								&lt;li&gt;&lt;a href="#"&gt;Animal Comes Alive&lt;/a&gt;&lt;/li&gt;
								&lt;li&gt;&lt;a href="#"&gt;The Hits&lt;/a&gt;&lt;/li&gt;
								&lt;li&gt;&lt;a href="#"&gt;Animal: Unplugged&lt;/a&gt;&lt;/li&gt;
							&lt;/ul&gt;
						&lt;/li&gt;
					&lt;/ul&gt;
				&lt;/li&gt;
				&lt;li&gt;&lt;a href="#"&gt;Lips&lt;/a&gt;&lt;/li&gt;
			&lt;/ul&gt;
		&lt;/li&gt;
		&lt;li&gt;&lt;a href="#"&gt;Gonzo&lt;/a&gt;&lt;/li&gt;
		&lt;li&gt;&lt;a href="#"&gt;Miss Piggy&lt;/a&gt;&lt;/li&gt;
		&lt;li&gt;&lt;a href="#"&gt;Fozzy&lt;/a&gt;&lt;/li&gt;
	&lt;/ul&gt;
</pre>

<p>In your scss or sass document, add the Menu and Clearfix mixin:</p>
<pre>
	// Clearfix
	@mixin clearfix {
		&:before, &:after { content: ""; display: table; }
		&:after { clear: both; }
		zoom: 1;
	}
	
	// Menu
	@mixin menu($parentLinkPadding: 10px 25px, $childLinkPadding: 8px 25px, $dropDownWidth: 180px) {
		margin: 0;
		padding: 0;
		li {
			float: left;
			list-style: none;
			position: relative;
			a { display: block; padding: $parentLinkPadding; text-decoration: none; }
		}
		li:hover > ul { display: block; }
		ul {
			display: none;
			left: 0;
			margin: 0;
			padding: 0;
			position: absolute;
			width: $dropDownWidth;
			li { float: none; }
			a { padding: $childLinkPadding }
			ul { left: $dropDownWidth; top: 0; }
		}
		@include clearfix;
	}
</pre>

<p>Next, apply the mixin to your containing unordered list and change the values for the parent links padding ($parentLinkPadding), child links padding ($childLinkPadding), and width of the drop down menus ($dropDownWidth). For example:</p>
<pre>
	// Basic setup
	ul {
		@include menu;
	}
	
	// or specifying different values for paddings and widths
	ul {
		@include menu(10px 45px, 8px 45px, 220px);
	}
</pre>

<p>Ta-da! This will give you basic drop down functionality. Feel free to add in styles for your lists, anchors, etc after the mixin call. For example:</p>

<pre>
	ul {
		// Initialize Menu 
		@include menu;
		
		// Style anchors within drop down
		a {
			background: red;
			color: #FFF:
		}
	}
</pre>

<h2>Latest Changes</h2>

<h3>1.0 - April 28, 2012</h3>
<ul>
	<li>Initial release. Hooray!</li>
</ul>