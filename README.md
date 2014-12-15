<h1>Gravity Forms Sticky List</h1>

Sticky List is a Gravity Forms add-on that lets you list and **edit entries** from the front end.

<h2>Description</h2>

#### Sticky List
Sticky List is an add-on for the WordPress plugin <a href="http://www.gravityforms.com/" target="_blank">Gravity Forms</a> that lets you list and edit entries from the front end. You can display a list on the front end where users can view, delete and edit submitted entries. 

#### Features

* Display a list of entries on the front end
* Choose who can se the list; entry creator, all logged in users or anyone.
* Support for multiple lists in the same page
* Support for (almost) all Gravity Forms fields
* Create/edit/delete Wordpress posts from the fron end
* Conditional logic support
* View, edit and delete existing entries from the front-end
* Conditional notifications
* Conditional confirmations
* List sorting and search (using <a href="http://www.listjs.com/">list.js</a>)
* Custom column labels
* Uses new <a href="http://www.gravityhelp.com/documentation/page/Gravity_Forms_API">Gravity Forms API</a> and the official <a href="http://www.gravityhelp.com/documentation/page/Add-On_Framework">Gravity Forms Add-on framework</a>
* Fully customizable with dead simple styles to override
* Fully localized. You can <a href="https://github.com/13pixlar/sticky-list/tree/master/languages">add your translation</a>
* Fully supported and maintained
* Completely free and open source

#### Planned features

* Support for multi page forms

#### List and edit Gravity Form entries on the front end

Front end editing of entries has allways been a problem in Gravity Forms. Solutions that exist are buggy and not very feature rich. Gravity Forms Sticky List aims to fill this gap and provide a simple and solid way to view, edit and delete entry submissions on the front end. The goal of the plugin is not to to display entries in a fancy way (excelent <a href="https://gravityview.co/">GravityViews</a> allready does that brilliantly) but to provide a simple, lightweight and rock solid way to list, edit and delete submissions on the front-end. Lists can be embedded in any post or page and you can have as many lists as you want in a single page.

#### Delete Gravity Form submissions from front end

Gravity Forms Sticky List uses a simple ajax approach to deleting entries. Deleted entries are moved to trash or permanently deleted depending on the per form settings. 

#### Sort and search entries

Sticky List uses the fast and lightweight <a href="http://www.listjs.com/">list.js</a> to allow for sorting the list and searching the entries. Searching entries is fast and results are updated immediately. 

#### Conditional confirmations and notifications

Gravity Forms Sticky List adds conditional confirmations and notifications so that different confirmations messages can be shown depending on if a new entry was submitted or if an existiong entry was updated, and diffrent email notifications can be sent if an entry was added, updated or deleted.

#### Styling the list

Sticky List ships with a minimal stylesheet that is easy to override. The table has the class of `.sticky-list` attached to it which can be used to override the default styles. The stylesheet is located in `sticky-list/css/sticky-list_styles.css` in the plugins main directory.

#### Usage

1. Upload and activate the plugin
2. Go to the settings page of a form and click the Sticky List settings tab
3. Enable Sticky List for that form att choose your settings
4. Go to the form editor and select what fields should be displayed in the list
5. Put the shortcode in a page/post with the corresponding form id, i.e `[stickylist id="1"]`

#### Developers
This is the fully documented version of the plugin. This plugin is Open Source and pull requests are welcome. The commenting in the main plugin file may seem excessive but I'm learing as I go and keeping the code comments detailed is a good way to remember exactly what every piece of code does. I hope that this will also be of help to anyone interested in contributing to the source code.

**Note:** <a href="http://www.gravityforms.com/" target="_blank">Gravity Forms</a> version 1.8.19.2+ is required for this plugin.

#### Known bugs

**Some fields are not updated**<br>
There is a bug in earlier versions the Gravity Forms API that prevents Sticky List from working correctly. Please update Gravity Forms. More information and fix, please see the FAQ section of this readme.

**File field does not display uploaded file when viewed or edited**<br>
This will be addressed in a future version of Sticky List.

#### Installation

1. Upload extracted folder to the '/wp-content/plugins/' directory
2. Activate the plugin through the 'Plugins' menu in WordPress
3. Choose the required Sticky List settings on the individual form settings page.

<h3>Frequently Asked Questions</h3>

<h5>The list is empty, why?</h5>

You need to check "Show in list" on the fields that you would like to appear in the list. This is done in the form editor when edtiting a field.

<h5>The View and Edit links don't do anything</h5>

In Sticky List settings for that form: make sure that you select the page/post where the FORM is embedded. The actual form is then used to view and/or edit the entries.

<h5>Where are the Sticky List settings?</h5>

Sticky List is activated on a per form basis. The settings are located in the individual form settings, right under Notifications.

<h5>I still cant find any sticky list settings</h5>

Make sure that the plugin is activated **and** that your Gravity Forms version is 1.8.19.2 or higher.

There is a bug in the Gravity Forms API in pervious versions that prevented fields from getting saved in the entry. The bug was fixed in version 1.8.19.2 of Gravity Forms. Make sure you use an <a href="http://www.gravityhelp.com/downloads/">updated version</a>. If you are not able to update Gravity Forms you can easily apply the patch manually to `plugins/gravityforms/includes/api.php`

On line `510`, remove 
```PHP
if (empty($entry_id))
    $entry_id = $entry["id"];
```
and replace with
```PHP
if (empty($entry_id)) {
    $entry_id = $entry["id"];
}else{
    $entry["id"] = $entry_id;
}
```

In that case, you also need to change the Sticky List plugin file to requre an earlier version of Gravity Forms

In `plugins/gravity-forms-sticky-list/sticky-list.php` on line `23` change 
```PHP
protected $_min_gravityforms_version = "1.8.19.2";
```
to you version of Gravity Forms. Note that this change will be lost when updating Sticky List. Therefore its absolutely recommended that you update Gravity Forms when using this plugin on a production site.

<h3>Changelog</h3>

**1.0.7**
* Added support for Post fields (create/edit/delete Wordpress posts).

**1.0.6**
* Updated confirmations to properly render merge tags.

**1.0.5**
* Fixed a nasty bug that prevented confirmation and notification settings from being displayed if Stickly List was active but not enabled for a form.

**1.0.4**
* Update: Added alphabetic sorting of pages/posts in embedd dropdown
* Update: Increased number of visible pages/posts in embedd dropdown
* Feature: Added the option to manually input am embedd url

**1.0.3**
* Fixed an issue where last name was displayed befor first name in the list
* Fixed an issue that prevented some confirmations from displaying
* Fixed som undefined index warnings

**1.0.2**
* Fixed a problem where dependencies would not get included

**1.0.1**
* Fixed an issue where only the first 20 entries in the list were shown
* Fixed a bug where translation would not get loaded

**1.0**
* Initial release
