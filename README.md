# View site

You can view the website on [https://dtai.cs.kuleuven.be/stories](https://dtai.cs.kuleuven.be/stories/)

# ML instructions: How to add new content

## 1. Fork the repository
Create a copy of the website repository by forking the repository to your own GitHub

## 2. Create a new article
1. Install Hugo
2. Run the following command, replacing "name_of_the_author" with your name and "name_of_the_post" with the post title

   `hugo new --kind post post/name_of_the_author/name_of_the_post`
   
   This will create the new page with the current date already filled
3. Go to `content/posts/name_of_the_author/name_of_the_post`
4. Edit the index.md with your post, written in Mark down

## 3. Add yourself as an author
If you're writing your first article, you should probably also make a nice author page for yourself.

1. Go to the `content/authors` folder
2. Copy the `demo` folder
3. Rename the folder to your name and lastname, separated with a dash, e.g. `luc-deraedt` (do not an underscore)
4. Update the `_index.md` file with your personal information

## 4. Send a pull request
Now go back to the main repository, and send a pull request from your forked repository.
One of the website admins will then pull your article in, and rebuild the website.

Thanks for posting about your research!

Website structure



# Website template information

[**Academic**](https://github.com/gcushen/hugo-academic) makes it easy to create a beautiful website for free using Markdown, Jupyter, or RStudio. Customize anything on your site with widgets, themes, and language packs. [Check out the latest demo](https://academic-demo.netlify.com/) of what you'll get in less than 10 minutes, or [view the showcase](https://sourcethemes.com/academic/#expo).

**Academic Kickstart** provides a minimal template to kickstart your new website.

- 👉 [**Get Started**](#install)
- 📚 [View the **documentation**](https://sourcethemes.com/academic/docs/)

## Ecosystem

* **[Academic Admin](https://github.com/sourcethemes/academic-admin):** An admin tool to import publications from BibTeX or import assets for an offline site
* **[Academic Scripts](https://github.com/sourcethemes/academic-scripts):** Scripts to help migrate content to new versions of Academic

## License

Copyright 2017-present [George Cushen](https://georgecushen.com).

Released under the [MIT](https://github.com/sourcethemes/academic-kickstart/blob/master/LICENSE.md) license.

[![Analytics](https://ga-beacon.appspot.com/UA-78646709-2/academic-kickstart/readme?pixel)](https://github.com/igrigorik/ga-beacon)
