=== Syndication Links ===
Contributors: dshanske
Tags: syndication, indieweb, indiewebcamp, POSSE, social media, sharing
Requires at least: 4.7
Tested up to: 4.9.5
Stable tag: 3.4.1
License: GPLv2 or later

A simple way to link to copies of your [cross-posted](https://indieweb.org/cross-posting) content in other social networks or websites.

== Description == 

It supports adding rel-syndication/u-syndication links to your posts, pages, and comments, indicating where a syndicated copy is. You can do this manually and some plugins support 
automatically adding their links as well.

== Screenshots ==

1. Example of Syndication Links metabox with links filled in
2. Example of output display on website

== Installation == 

1. Upload the folder 'syndication-links' to the '/wp-content/plugins/' directory
2. Activate the plugin through the 'Plugins' menu in WordPress

== Privacy and Data Storage Information ==

This plugin stores syndication links, which can be attached to any post, page, or comment. They can be added to custom post types by filter. 

For webmention initiated comments, this information
will be added by parsing the source of the webmention. It is assumed if you send a webmention, you consent to share this information if it is publicly shared on your page. Our recommendation
is that site owners should take down information on request. 

For comments initiated on the site, there is built-in way to add these links. For posts, they are typically added by retrieving information stored by other plugins for display. It is assumed
that by installing this plugin, as its intent is to display these links, that you wish to display them.

== Settings ==

Settings for the Syndication Links plugin can be found in the main WordPress "Settings" tab in the
admin dashboard, or if the [Indieweb plugin](https://wordpress.org/plugins/indieweb) is installed, under the Indieweb tab. The options provided allow for various ways of presenting the syndication links in posts. Syndication Links by default will add links to the content. You can remove this in your plugin if you wish to call the display function directly.

The settings include the following options as follows with either a set of buttons, a check box (with a check indicating that the feature is "on") or an optional text field:

* **Display Text** -  Offers options to display text only, icons only, icons and text, and no display(hidden icons).
* **Size** - Choice of small, medium, or large size icons.
* **Black Icons** - Checking the box defaults to a "black" social media icon set. 
* **Show on Front Page, Archive Page, and Search Results** - If checked the icons will show on pages other than a single view. If not checked, the icons will be hidden by the links will remain.
* **Show on Feed** - If checked the icons will show in your RSS feed as well
* **Text Before Links** - This is the text that appears before the Display Text/Icons (as indicated above). The default text is "Syndicated to:" but can be modified if desired.


**Note**: The particular CSS of your theme may change the display and output of the text and some of the icons.

== Supported POSSE plugins and implementations ==

The plugin supports automatically pulling data from plugins that syndicate your content so you don't need to do it manually. For anything not built in, integation is easy with a simple filter for potential use with any other plugin.

* [Bridgy](https://wordpress.org/plugins/bridgy-publish) - Simple user interface for Bridgy Publish
* [Social Networks Autoposter](https://wordpress.org/plugins/social-networks-auto-poster-facebook-twitter-g/) - Syndication Links supports Twitter, Facebook, and Tumblr since version 1.0.0
* [Medium](https://wordpress.org/plugins/medium/) - Syndication Links supports since version 3.0.5
* [Tumblr Crosspostr](https://wordpress.org/plugins/tumblr-crosspostr) - Supports Syndication Links since version 0.8.1
* [WordPress Crossposter](https://wordpress.org/plugins/wp-crosspost) - Supports Syndication Links since version 0.3.2
* [Diaposter](https://wordpress.org/plugins/diasposter/) - Supports Syndication Links since version 0.1.8

== Frequently Asked Questions ==

= How do I prevent the links from being automatically added to the content? =

You will have to remove the content filter `remove_filter( 'the_content', array( 'Syn_Config', 'the_content' ) , 30 )` and then you can call get_syndication_links() directly in your theme.

* `get_syndication_links( $object, $args ) - Returns the HTML for $object. $object can be a post_ID, a WP_Post object, or a WP_Comment object.
** $args
*** `style` - Defaults to ul
*** `text` - Display text, defaults to settings option
*** `icons` - Display icons, defaults to settings option
*** `container-css` - Class to wrap entire syndication links in
*** `single-css` - Class to wrap a single link in
*** `text-css` - Class to wrap the text before the links in

= How can I look up the original if I have a syndication link? =

If you add `?original-of=` and the URL-encoded URL it will return the post that has that URL stored. As no two posts should have the same two syndication links it will by default only return the first.

= What filters are available to modify output? =

* `syn_rewrite_secure( $domains )` - $domains is an array of domain names to rewrite to https if found
* `syn_metabox_types( $screens )` - $screens would be an array of post types to add the Syndication Link metabox to.
* `syn_network_strings( $strings )` - $strings is an array of descriptive text strings by domain name
* `syn_add_links( $urls, $post_ID )` - $urls is an array of retrieved links from $post_ID
* `syn_links_display_defaults( $defaults )` - Filter the defaults for displaying Syndication Links

== Upgrade Notice == 

= Version 3.0.5 =

Upgrade to this version moves the location of stored syndication links to match the changes in the Micropub plugin. Recommend
that all users back up prior to upgrade in the event of accidental corruption.

= Version 3.0 =

Version 3.0 removes the two sets of icon fonts in favor of SVG icons. If this is a concern, do not upgrade at this time. Version 3.0 also removes
rel-me support from this plugin as this support is being built into the Indieweb plugin. Please install that.

= Version 3.2.2 = 

Removes H-Card Widget as does not fit into this plugin. Moving over to the Indieweb plugin although there is a possibility it may not stay there.

== Credits ==

In no particular order...

1. The [Indieweb](https://indieweb.org) community of users and all users of this plugin 
2. [Meitar Moscovitz](https://github.com/meitar) for fixes and code contributions related to support of the plugin in his various plugins.
3. Justin Tadlock for the initial [Social Icons](http://justintadlock.com/archives/2013/08/14/social-nav-menus-part-2) design.
4. Jihaisse and Peter Molnar for the [SNAP](https://wordpress.org/plugins/social-networks-auto-poster-facebook-twitter-g/), courtesy of [WordPress Syndication](https://github.com/jihaisse/wordpress-syndication)
5. [Simple-Icons](https://https://simpleicons.org/) for their icon packs for logos. Simple Icons is licensed under CC0 v1.0 Universal.
6. [Genericons Neue](http://genericons.com/) for their generic icon packs. Genericons Neue is licensed under the GPLv2.
7. [Chris Aldrich](http://stream.boffosocko.com) for many suggestions on improving the display and for screenshots.
8. [PHPCS](https://github.com/squizlabs/PHP_CodeSniffer) is used with the [WordPress](https://github.com/WordPress-Coding-Standards/WordPress-Coding-Standards) and [PHP Compatibility](https://github.com/wimg/PHPCompatibility) Standards in order to ensure compatibility with supported versions of PHP and enact WordPress Coding Standards.
9. [Travis-CI](https://travis-ci.org) is used to actively test against various PHP versions

== Changelog ==

= Version 3.4.1 ( 2018-05-06 )
* Refresh Simple Icons
* Remove internationalization of icon names
* Update development environment
* Add Syndication data to JSONFeed
* Do not add syndication information to the content of a jsonfeed
* Add privacy policy and export data support for WordPress 4.9.6
* Add privacy notice to readme

= Version 3.4.0 ( 2018-03-03 )
* Updated Simple Icons to latest version
* Switched Genericons Neue to a submodule as the svg version was not distributed in the npm package
* Added support for Mastodon Auto Post per request. Unable to test due not using same
* Added support for Keyring Social Importer. Unable to test due not using same
* Simplified saving of metadata
* Changed Metabox to a dynamically generated array

= Version 3.3.2 ( 2018-02-03 )
* Updated Simple Icons to latest version

= Version 3.3.1 ( 2018-01-04 )
* Updated Simple Icons to latest version
* Support for pulling data out for SNAP out of Post Meta without dependence on SNAP classes

= Version 3.3.0 ( 2017-12-?? )
* Switched to Simple Icons as larger, updated, and maintained more frequently than Automattic's Social Icons repo
* Added in the Genericon Neue pack for when there is no logo for a site with a series of generic icons
* SVG Sprite only will be distributed instead of individual SVG files
* Icon colors automatically generated from Simple Icons repository
* Icon names automatically generated from Simple Icon repository
* New code to try and find an icon without hard coding the domain to icon relationship by trying to find the icon name inside the domain string.
* Development tools now configured for bringing in PHPCS Coding Standards and generating new files
* Screenshots!
* License information included for the plugin as well as dependencies
* Again, automation automation automation

= Version 3.2.4 ( 2017-11-23 )
* Changelog will now note a release date
* Added/redid colors for many links

= Version 3.2.3 =
* Remove Social Support as Plugin is no longer listed in WordPress repository
* Add additional syndication icons
* Fix textdomain issues
* Add PHP Compatibility tests and textdomain tests
* PHPCS Improvements
* Add setting for disabling links in feed

= Version 3.2.2 =
* Remove H-Card Widget

= Version 3.2.1 =
* Break add `get_syndication_links function` into smaller pieces ( props @Ruxton )
* Adds `get_syndication_links_elements` which returns array of anchor tags
* Adds `get_syndication_links_display_defaults` to return default options
* Adds `get_syndication_links_text_before` to return textbefore on it's own

= Version 3.2.0 =
* Add support for comment syndication links
* Add CSS for styling text before

= Version 3.1.1 = 

* Fix documentation re priority of content filter
* Remove empty check as interfering with filter
* Add uniqueness check after filter

= Version 3.1.0 = 

* Cleanup of settings attributes using enhancements available in WordPress 4.7
* Individual SVG icons and code to generate an SVG sprite now included in the plugin
* Option to have hidden links now available
* Small Medium and Large CSS files are included by option - generated by sass
* Option to disable links being added to content removed as they can now be hidden. Any theme that wants to call the display function directly will have to remove the content filter
* Add arguments to `get_syndication_links` to allow for customized presentation
* Adding `?original-of=url` with url being the syndication URL will return the original entry.

= Version 3.0.5 =

* Change storage of syndication links in order to match Micropub plugin. Storage is now array
* Remove old property once migrated to new
* Remove JSON REST filter as deprecated
* Add support for the official Medium plugin per request @chrisaldrich

= Version 3.0.4 = 

* Compatibility update
* Add textdomain for language support

= Version 3.0.2 = 
	* Adjust close bracket

= Version 3.0.1 = 
	* Fix text display issue

= Version 3.0.0 =
	* Remove icon fonts in favor of SVG
	* Remove rel-me support to move to implementation in Indieweb plugin
	* Remove h-card support to move to implementation in Indieweb plugin (it wasn't very good anyway)
	* Introduce new get_syndication_data function to abstract out storage

= Version 2.1.0 = 
	* Removed user meta code

= Version 2.0.3 = 
	* Minor Tweaks and Cleanup

= Version 2.0.2 =
	* CSS fixes
	* Version number added to CSS import to avoid caching on update

= Version 2.0.1 = 
	* Misc. Bug Fixes
	* Bridgy Publish Support removed - new Bridgy plugin will handle that

= Version 2.0.0 = 
	* Rewritten to remove global scoping
	* Option to add URLs to the head of the home page for rel-me auth
	* Option to add URLs as a widget for rel-me auth

= Version 1.0.3 = 
	* Security Fix. Nothing new
= Version 1.0.2 =
	* Refinements
	* Add support for pages and a filter to add additional content types
= Version 1.0.0 =
	* Refinements
	* Addition of h-card widget. 
	* Improvements to hooks
	* Addition of automatic information from SNAP and Social(courtesy WordPress Syndication). 
	* Now supports second font choice and choice of color or black.
= Version 0.6.0 = 
	* Add hooks and functions to allow additional urls to  be added
= Version 0.5.0 =
	* Clean up the plugin for initial release to WordPress repository.
= Version 0.5 = 
	* Moved to simplified data structure. 
	* Hidden migration function
= Version 0.4 =
	* Rewriting using Grunt/SASS for more flexibility
= Version 0.3 =
	* Customizable Networks finished. 
	* Changed social icons CSS to automatically add only if the class for the list has social-icon in it.
= Version 0.2 = 
	* Settings Screen rewritten using WordPress Settings API. 
	* Going to rewrite with customizable networks and thus option to disable sites you do not syndicate to. 
	* Added social icons CSS to automatically add icons to anything in a <LI>
= Version 0.1 =
	* Forked from the Semantic Comments plugin. Start of configurable options.
