Jekyll-to-Ghost Exporter (Updated version)
========================

*Note as of 5/3/2019*: This is an updated version of what [mattvh](https://github.com/mattvh/Jekyll-to-Ghost) posted. I've integrated some changes so that it can easily export a Jekyll site to Ghost 2.14.0.

Want to export your Markdown posts from [Jekyll](http://jekyllrb.com) to a format that can be easily imported into [Ghost?](http://ghost.org) This plugin will help you do that, though there are some limitations. It doesn't handle static pages, and it doesn't do anything with images. You'll have to copy those over yourself and manually adjust any URL differences.

This was built by reverse-engineering the WordPress exporter [plugin](http://wordpress.org/plugins/ghost/) to match the JSON file it outputs.


Installation
------------

0. Clone the repo and drop the `jekylltoghost.rb` file into your Jekyll site's `_plugins` directory
1. Run `jekyll build`.
2. There should now be a `ghost_export.json` file in the `_site` directory.
3. Follow the Ghost guide [here](https://docs.ghost.org/api/migration/#converting-html) to convert the HTML block into **Mobiledoc** (this is what the new Ghost blog accepts).
4. Download the JSON file, (optional) edit the `users` section, and import it in your Ghost dashboard.

I'm still working on automatically extracting author information from site data folder, but in the mean time a workaround would be manually fill the info below and paste it to the `users` block in the converted JSON file ([source](https://docs.ghost.org/api/migration/#example)):

```
"users": [
            {
                "id":           3,
                "name":         "Jo Bloggs",
                "slug":         "jo-blogs",
                "email":        "jo@example.com",
                "profile_image": null,
                "cover_image":   null,
                "bio":           null,
                "website":       null,
                "location":      null,
                "accessibility": null,
                "meta_title":    null,
                "meta_description": null,
                "created_at":    1283780649000,
                "created_by":    1,
                "updated_at":    1286958624000,
                "updated_by":    1
            }
        ],
```


License
-------

This Jekyll plugin is licensed under the MIT license.
