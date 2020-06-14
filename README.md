Styling Scrollbars with CSS: The Modern Way to Style Scrollbars
William Le
Since the early days of the web, customizing the browser’s scrollbar has proven to be very difficult to standardize across major browsers. Fortunately, on September 2018 a W3C Working Draft called CSS Scrollbars was released that looks like a viable way to finally accomplish this!

Styling the scrollbar in the browser can be an valuable way to communicate a company’s brand. For example, styling the Alligator.io website’s scrollbars could look like this:

Alligator.io custom scrollbar style screenshot

Throughout the years, there emerged many ways to accomplish this. Microsoft Internet Explorer was one of the first vendors to provide a CSS API for this, but many indie developers were so frustrated to find a solution that they created various solutions with JavaScript.

Fast-forward to today, now that Internet Explorer is slowly being replaced by Microsoft Edge, it just boils down to 2 approaches:

Chrome/Edge/Safari: using -webkit-scrollbar
Firefox: uses the new CSS Scrollbars API (eg., scrollbar-color and scrollbar-width) spec.
Let’s jump into some code samples!

The JavaScript solutions fall short since they have difficulty emulating high-end behaviors like inertia scrolling (eg., decaying motion when scrolling via trackpads). 😭

Scrollbars in Chrome/Edge/Safari
Styling scrollbars for Chrome/Edge/Safari is available behind the vendor prefix -webkit-scrollbar

body::-webkit-scrollbar {
  width: 12px;               /* width of the entire scrollbar */
}
body::-webkit-scrollbar-track {
  background: orange;        /* color of the tracking area */
}
body::-webkit-scrollbar-thumb {
  background-color: blue;    /* color of the scroll thumb */
  border-radius: 20px;       /* roundness of the scroll thumb */
  border: 3px solid orange;  /* creates padding around scroll thumb */
}
webkit-styled scrollbars

But there’s good news… And bad news:

Good news! This code works 👌 perfectly fine in the latest releases of Chrome/Edge/Safari!

Bad news? Unfortunately, this spec has been formally abandoned by W3C so we can expect it to be slowly deprecated in the coming years.

Microsoft Edge officially switched to the Chromium V8 engine on January 2020!

Scrollbars in Firefox
Firefox is a champion of new W3C standards, and they’re always willing to try out emerging APIs. As such, the new CSS Scrollbars features are already available in normal releases of Firefox:

body {
  scrollbar-width: thin;          /* "auto" or "thin"  */
  scrollbar-color: blue orange;   /* scroll thumb & track */ 
}
scrollbars on firefox

Sweet! You might have noticed a few differences compared to the deprecated -webkit-scrollbar spec.

Firstly, it’s way more concise! And secondly, it lacks features like creating a padding and roundness for the “track thumb”. Since the spec is still changing, these missing features could likely get included.

The Way Forward
How do we style scrollbars considering there isn’t a single, authoritative API? Just combine both approaches!

/* The emerging W3C standard
   that is currently Firefox-only */
* {
  scrollbar-width: thin;
  scrollbar-color: blue orange;
}

/* Works on Chrome/Edge/Safari */
*::-webkit-scrollbar {
  width: 12px;
}
*::-webkit-scrollbar-track {
  background: orange;
}
*::-webkit-scrollbar-thumb {
  background-color: blue;
  border-radius: 20px;
  border: 3px solid orange;
}
Once -webkit-scrollbar is deprecated, you can fallback on the new CSS Scrollbars standard without missing a beat.
