# Permalinks Customizer

## Description

Customize your URL and set the slug. You can use basic keywords which is defined by the WordPress for defining the permalinks as well as someother new keywords which is defined by this plugin. All the keywords are defined on the Tags page under Permalinks Customizer.

By using **Permalinks Customizer** you can set the different permalink structure for each and every PostType and Taxonomy.

### How to set the Permalinks for the PostTypes separately

Let's assume that you have 6 <strong>PostTypes</strong> and they all have different style of <strong>permalinks</strong>. Like:

* **Blog** : For this post type you want to create a **permalink** which looks like this: http://www.example.com/blog/year-month-date-postname/
* **Customers** : For this post type you want to create a **permalink** which looks like this: http://www.example.com/customers/postname/
* **Events** : For this post type you want to create a **permalink** which looks like this: http://www.example.com/events/year-month-date-postname/
* **Press** : For this post type you want to create a **permalink** which looks like this: http://www.example.com/press/category/year/postname/
* **News** : For this post type you want to create a **permalink** which looks like this: http://www.example.com/news/year/postname/
* **Sponsors** : For this post type you want to create a **permalink** which looks like this: http://www.example.com/company/sponsor/post_title/

This plugin allows you to do this very easily. You just need to go on **Permalinks Customizer** Settings Page. Where text fields are shown with PostType name. You can define your permalinks you want to create for each post type.

If you leave any PostType field empty. So, **Permalinks Customizer** would create a permalink for that PostType by using the default **permalink** settings.

### How to Configure Permalinks Customizer

> You can configure the plugin by going to the menu `Permalinks Customizer` that appears in your admin menu.<br><br>**OR**<br><br> You can directly access it from: http://www.example.com/wp-admin/admin.php?page=permalinks-customizer-posts-settings

## Structure Tags

### Default WordPress Tags

| Tag Name  | Description |
| ------------ | ------------- |
| %year% | The year of the post, four digits, for example 2004. |
| %monthnum% | Month of the year, for example 05. |
| %day% | Day of the month, for example 28. |
| %hour% | Hour of the day, for example 15. |
| %minute% | Minute of the hour, for example 43. |
| %second% | Second of the minute, for example 33. |
| %post_id% | The unique ID # of the post, for example 423. |
| %postname% | A sanitized version of the title of the post (post slug field on Edit Post/Page panel). So "This Is A Great Post!" becomes this-is-a-great-post in the URI. |
| %category% | A sanitized version of the category name (category slug field on New/Edit Category panel). Nested sub-categories appear as nested directories in the URI. |
| %author% | A sanitized version of the author name. |

### Custom Tags for PostTypes 

| Tag Name  | Description |
| ------------ | ------------- |
| %title% | Title of the post. let's say the title is "This Is A Great Post!" so, it becomes this-is-a-great-post in the URI. |
| %parent_postname% | A sanitized version of the title of the post (post slug field on Edit Post/Page panel). So "This Is A Great Post!" becomes this-is-a-great-post in the URI. This <strong>Tag</strong> contains Immediate <strong>Parent Page Slug</strong> if any parent page is selected before publishing. |
| %child-category% | A sanitized version of the category name (category slug field on New/Edit Category panel). |
| %product_cat% | A sanitized version of the product category name (category slug field on New/Edit Category panel). Nested sub-categories appear as nested directories in the URI. <i>This <strong>tag</strong> is specially used for WooCommerce Products.</i> |
| &lt;%ctax_custom_taxonomy%&gt; | A sanitized version of the custom taxonomy where the taxonomy name is **_custom_taxonomy_**. Replace the _custom_taxonomy_ with your appropriate created taxonomy name. If you want to provide the default slug which is used when the category/taxonomy doesn\'t be selected so, make sure to provide default name/slug which looks like this: **_&lt;%ctax_custom_taxonomy??sales%&gt;_**. Value which is written between the **_??_** and **_%&gt;_** is used as default slug. |
| &lt;%ctaxparents_custom_taxonomy%&gt; | A sanitized version of the custom taxonomy where the taxonomy name is **_custom_taxonomy_**. Replace the _custom_taxonomy_ with your appropriate created taxonomy name. If you want to provide the default slug which is used when the category/taxonomy doesn\'t be selected so, make sure to provide default name/slug which looks like this: **_&lt;%ctaxparents_custom_taxonomy??sales%&gt;_**. Value which is written between the **_??_** and **_%&gt;_** is used as default slug. This tag almost has the same functionality as _&lt;%ctax_custom_taxonomy%&gt;_ the only difference is that it appends all the parent slugs of the selected category/term which doesn\'t be the case in _&lt;%ctax_custom_taxonomy%&gt;_. |
| %author_firstname% | A sanitized version of the author first name. If author first name is not available so, it uses the author\'s username. |
| %author_lastname% | A sanitized version of the author last name. If author last name is not available so, it uses the author\'s username. |

**Note**: *%postname%* is similar as of the *%title%* tag but the difference is that *%postname%* can only be set once whereas *%title%* can be changed. let's say the title is "This Is A Great Post!" so, it becomes "this-is-a-great-post" in the URI(At the first time, *%postname%* and *%title%* works same) but if you edit and change title let's say "This Is A WordPress Post!" so, *%postname%* in the URI remains same "this-is-a-great-post" whereas *%title%* in the URI becomes "this-is-a-wordpress-post"

### Custom Tags for Taxonomies 

| Tag Name  | Description |
| ------------ | ------------- |
| %name% | Name of the Term/Category. let's say the name is "External API" so, it becomes external-api in the URI. |
| %term_id% | The unique ID # of the Term/Category, for example 423 |
| %slug% | A sanitized version of the name of the Term/Category. So "External API" becomes external-api in the URI. |
| %parent_slug% | A sanitized version of the name of the Term/Category. So "External API" becomes external-api in the URI. This Tag contains Immediate Parent Term/Category Slug if any parent Term/Category is selected before adding it. |
| %all_parents_slug% | A sanitized version of the name of the Term/Category. So "External API" becomes external-api in the URI. This Tag contains all the Parent Term/Category Slug if any parent Term/Category is selected before adding it. |

**Be warned**: *This plugin is not a replacement for WordPress's built-in permalink system*. Check your WordPress administration's "Permalinks" settings page first, to make sure that this doesn't already meet your needs.

## Filters

### Exclude Permalinks

If you want to exclude some Permalink to processed with the plugin so, just add the filter looks like this:
```
function yasglobal_exclude_url( $permalink ) {
  if ( false !== strpos( $permalink, '/contact-us/' ) ) {
    return '__true';
  }
  return;
}
add_filter( 'permalinks_customizer_exclude_request', 'yasglobal_exclude_url' );
```

### Show Relative Permalink/URL

To show relative permalink/url in Edit Post, add this filter in your themes functions.php.
```
add_filter( 'permalinks_customizer_remove_home_url', '__return_true' );
```

### Exclude PostType from the Plugin

To exclude the plugin to be worked on any PostType. Add this filter in your themes functions.php.

```
function yasglobal_exclude_post_types( $post_type ) {
  if ( $post_type == 'page' ) {
    return '__true';
  }
  return '__false';
}
add_filter( 'permalinks_customizer_exclude_post_type', 'yasglobal_exclude_post_types');
```
**Note**: Plugin stops working on the backend. *No more permalinks* would be generated by the plugin but the permalink which are already created will remains in work.

### Disable automatically create redirects

To disable automatically create redirects feature on creating and updating the post/pages/categories, add this filter in your themes functions.php.
```
add_filter( 'permalinks_customizer_auto_created_redirects', '__return_false');
```
This filter stops to be creating new redirects but existed redirects keeps working. To stop existed redirects, add [this](#disable-redirects) filter.

### Disable Redirects

To disable redirects to be applied , add this filter in your themes functions.php.
```
add_filter( 'permalinks_customizer_disable_redirects', '__return_false');
```
This filter only stop redirects to be work but the automatically create redirects still works. To stop automatically create redirects feature add [this](#disable-automatically-create-redirects) filter.

### Thanks for the Support

The support from the users that love Permalinks Customizer is huge. You can support Permalinks Customizer future development and help to make it even better by giving a [5 star rating with a nice message](https://wordpress.org/support/plugin/permalinks-customizer/reviews/?rate=5#new-post) to me :smiley:

## Installation

This process defines you the steps to follow either you are installing through WordPress or Manually from FTP.

## From within WordPress

1. Visit 'Plugins > Add New'
2. Search for Permalinks Customizer
3. Activate Permalinks Customizer from your Plugins page.
4. Go to [after activation](#after-activation) below.

## Manually

1. Upload the `permalinks-customizer` folder to the `/wp-content/plugins/` directory
2. Activate Permalinks Customizer through the 'Plugins' menu in WordPress
3. Go to [after activation](#after-activation) below.

### After activation

1. Go to the plugin settings page and set up the plugin for your site.
2. You're done!

## Frequently Asked Questions

**Q. How to define Settings for the PostType?**

A. Go to WordPress Dashboard under Permalinks Customizer, Go to PostTypes Settings Page, there is a textfield for all the available PostType. On this field, you can define structure which is used for this PostType.

**Q. Can i use tags in PostType Settings?**

A. Yes, you can use any tag as defined on the [Permalinks Customizer page](https://wordpress.org/plugins/permalinks-customizer/) under the *TAGS FOR POSTTYPES* heading.

**Q. Does the plugin supports custom taxonomy tag?**

A. Yes, it supports custom taxonomy tag. You can define the tag as mentioned on the [Permalinks Customizer page](https://wordpress.org/plugins/permalinks-customizer/).

**Q. Can i see the created permalinks for the PostType?**

A. Yes, you can see all the created permalinks on the PostType Permalinks Page under Permalinks Customizer.

**Q. How to define Settings for the Taxonomies?**

A. Go to WordPress Dashboard under Permalinks Customizer, Go to Taxonomies Settings Page, there is a textfield for every available Taxonomies. On this field, you can define structure which is used for this Taxonomy.

**Q. Can i use tags in Taxonomies Settings?**

A. Yes, you can use any tag as defined on the [Permalinks Customizer page](https://wordpress.org/plugins/permalinks-customizer/) under the *TAGS FOR TAXONOMIES* heading.

**Q. Can i see the created permalinks for the Taxonomies?**

A. Yes, you can see all the created permalinks on the Taxonomies Permalinks Page under Permalinks Customizer.

**Q. Can i regenerate all the permalinks according to the defined structure?**

A. Yes, you can regenerate all the permalinks according to the defined structure. To have a bulk permalink update, Go to the *All Post* page there is a a option in the bulk action drop down with the name of `Regenerate Permalinks`. Use that option for regenerating the Permalinks.

**Q. Does *Regenerate Permalinks* damage my site SEO?**

A. No, it won't damage your site SEO. As regenerating permalinks added redirect against their previous permalink.

**Q. Can i see the available redirects?**

A. Yes, you can see the all the redirects created by this plugin from the Redirects Page under the Permalinks Customizer in the WordPress Dashboard.

**Q. Can i disable/delete redirects?**

A. Yes, you can disable/delete the redirects from the Redirects Page using Bulk Action.

**Q. Can i exclude PostType from the Plugin?**

A. Yes, you can exclude any posttype from the plugin to be worked on. For this just add the filter as shown [here](#exclude-posttype-from-the-plugin).
