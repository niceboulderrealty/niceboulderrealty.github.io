Welcome to the Github Pages repository for Nice Boulder's website [https://niceboulder.com](https://niceboulder.com). This README gives step-by-step instructions to create new web content and update the website.

# Creating New Web Content

Write your content into a text file using [Markdown](https://www.markdownguide.org/basic-syntax) formatting commands, and save each page or post as a separate ASCII .txt or .md file. Do **not** save in other formats such as Word (.doc or .docx) or Rich text (.rtf) -- these aren't compatible. To embed images, reference the image's filename using Markdown (as shown in the example below) and send the image files along with the markdown file to be published.

Markdown is a simple formatting language that enables creating content using a basic text editor such as macOS `TextEdit` or Windows `Notepad`. For example, the text file:

```
# Header

This paragraph includes *italics* and **bold** formatting.

1. Item one
2. Item two

| Column 1 | Column 2 |
|----------|----------|
| A        | B        |
| C        | D        |

![Markdown Everywhere](assets/images/content/2023-02-10-markdown-everywhere.webp)
```

is rendered on the website as:

> # Header
>
> This paragraph includes *italics* and **bold** formatting.
>
> 1. Item one
> 2. Item two
>
> | Column 1 | Column 2 |
> |----------|----------|
> | A        | B        |
> | C        | D        |
> 
> ![Markdown Everywhere](assets/images/content/2023-02-10-markdown-everywhere.webp)

You can optionally use a specialized Markdown editor. Here's some free ones to consider.

|     App     |    Platform    |                  Features                  |              Download             |
|-------------|----------------|--------------------------------------------|-----------------------------------|
| HackMD      | Web            | Realtime collaboration, GitHub integration | https://hackmd.io                 |
| StackEdit   | Web            | Web-based, formatting toolbar              | https://stackedit.io              |
| Dillinger   | Web            | Web-based, minimalistic                    | https://dillinger.io              |
| MacDown     | Mac            | Native app, formatting toolbar             | https://macdown.uranusjr.com      |
| Ghostwriter | Mac, PC, Linux | Multiple writing modes, feature-rich       | https://kde.github.io/ghostwriter |

The following guides are useful for learning Markdown. The first one contains everything you need to get started.

* [Markdown Basic Syntax](https://www.markdownguide.org/basic-syntax) lists the most common formatting commands
* [Jekyll Markdown Guide](https://www.markdownguide.org/tools/jekyll) identifies Markdown features supported by Jekyll
* [Kramdown Quick Reference](https://kramdown.gettalong.org/quickref.html) is the official guide for the Kramdown-flavored Markdown
* [Jekyll Cheatsheet](https://devhints.io/jekyll) for more advanced syntax

# Publishing to the Website

You need to install web development software in order to update the website. Fortunately everything is free thanks to open source software. The following instructions explain how to setup your computer and update the website using command-line tools. Some experience using a Terminal / command-line shell is helpful.

## Step 1: Install Web Development Tools

If you use a Mac:

1. Install [Xcode](https://apps.apple.com/us/app/xcode/id497799835?mt=12) from the App Store.

2. Launch Xcode, approve everything that it prompts you to install (such as "additional Xcode components", "command-line tools", etc.), then exit Xcode.

3. Launch Terminal (located in `Applications/Utilities`) and execute:
	* `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"` to install [Homebrew](https://brew.sh).
	* `brew install git rbenv ruby-build` to install [Git](https://git-scm.com) and [RBEnv](https://github.com/rbenv/rbenv#readme).

4. Quit Terminal, then immediately re-launch it and execute:
	* `rbenv install 3.1.3` to install [Ruby](https://www.ruby-lang.org) version 3.1.3.
	* `gem install jekyll bundler` to install [Jekyll](https://jekyllrb.com) and [Bundler](https://bundler.io).
	* `bundle install` to install everything else.

If you use a PC, then there's a bit of bad news: Jekyll and other development tools are not officially supported on Windows. Therefore, you have two choices:

1. Install Ruby and Jekyll on Windows using these [step-by-step instructions](https://jekyllrb.com/docs/installation/windows). This may work but YMMV.

2. Use Linux on your PC, for example install [Ubuntu](https://ubuntu.com) inside [VirtualBox](https://www.virtualbox.org), then setup the dev tools in Ubuntu. This works and is a popular choice amongst web developers, but it requires significiantly more technical expertise and is out of scope for this README.

## Step 2: Download The Website

1. Create a free GitHub account at [https://github.com](https://github.com), and share your username with the org admin to be granted access to this repository.

2. Once you have access, launch Terminal and execute:
	* `git clone https://github.com/niceboulderrealty/niceboulderrealty.github.io.git` to download the website.

3. Test to confirm everyting works:
	* `cd niceboulderrealty.github.io` to go to your local copy of the website.
	* `bundle exec jekyll serve --livereload` to run the website from your local computer.
	* Open [http://localhost:4000](http://localhost:4000) from your computer to view the website running locally.

If you see the Harvest Junction website at http://localhost:4000, then congratulations! You've setup your web development environment.

## Step 3: Update the Website Locally

Launch Terminal, `cd niceboulderrealty.github.io` to go to your local copy of the website, and execute:

1. `git pull` to download any recent updates to the website.

2. Update new markdown files to ensure they include the necessary [YAML front matter](https://jekyllrb.com/docs/front-matter) at the top. For example, a newsletter could include:

	```
	---
	title: "Newsletter"
	description: "Spring 2024 Edition (March - May)"
	authors: ["Chris Russell"]
	date: 2024-03-01
	
	categories: ["Newsletter"]
	image: "/assets/images/meta/newsletter-banner.webp"
	thumbnail: "/assets/images/meta/newsletter-16:9.webp"
	---
	```

	When in doubt, copy and update the front matter from similar posts or pages.

3. Name and copy new markdown files as follows:

 |   Contents  |                                Filename                                |
 |-------------|------------------------------------------------------------------------|
 | FAQ         | `collections/_faqs/NAME.md`                                            |
 | News        | `collections/_posts/YYYY-MM-DD-NAME.md`                                |
 | Project     | `collections/_projects/NAME.md`                                        |
 | Service     | `collections/_services/NAME.md`                                        |
 | Team member | `collections/_team/FIRSTNAME-LASTNAME.md` and edit `_data/authors.yml` |

4. Scale, format, and save images as follows:

 |     Contents     |  Resolution  |         Image Format         |                   Filename                   |
 |------------------|--------------|------------------------------|----------------------------------------------|
 | Favicon          | Varying      | PNG or ICO                   | See README in `assets/images/favicons`       |
 | Hero banner      | Varying      | WebP compressed best quality | `assets/images/meta/NAME-hero.webp`          |
 | Icon             | 100 x 100    | WebP uncompressed            | `assets/images/meta/icon-NAME-100.webp`      |
 | Logo             | Varying x 60 | WebP uncompressed            | See README in `assets/images/meta`           |
 | Page content     | Varying      | WebP (compressed as needed)  | `assets/images/content/YYYY-MM-DD-NAME.webp` |
 | Partners         | Varying      | WebP uncompressed or SVG     | `assets/images/partners/NAME.webp` or `.svg` |
 | Posts banner     | 1600 x 450   | WebP compressed high quality | `assets/images/meta/NAME-banner.webp`        |
 | Team headshot    | 400 x 400    | WebP compressed best quality | `assets/images/team/FIRSTNAME-LASTNAME.webp` |
 | Thumbnail (16:9) | 1240 x 698   | WebP compressed high quality | `assets/images/meta/NAME-16:9.webp`          |
 | Title (3:2)      | 1240 x 827   | WebP compressed high quality | `assets/images/meta/NAME-3:2.webp`           |

5. `bundle exec jekyll serve --livereload` to run the website from your local computer. Add `--drafts` to include posts in the `_drafts` folder, and `--future` to include posts dated in the future.

6. Open the website from [http://localhost:4000](http://localhost:4000) and review the new pages.

7. Make any necessary edits. Your changes are updated in realtime to your web browser.

## Step 4: Publish Changes to Github

1. `bundle exec jekyll build` to confirm the website builds locally without errors.

2. `git add .` to stage new and edited files to your local repository.

3. `git status` to review all changes to be committed. **Fix any issues before proceeding!** For example, if `git status` lists files or changes that should not be committed, then remove them using `git reset FILENAME` or `git restore FILENAME`.

4. `git commit -m "DESCRIPTION OF CHANGES"` to commit changes locally.

5. `git push` to upload changes to GitHub and publish to the website.

6. Monitor Github's [workflow dashboard](https://github.com/niceboulderrealty/niceboulderrealty.github.io/actions) to confirm the updates are built without errors. If an error occurs, then open the workflow and re-run the failed job. If it continues to fail, then re-run with debug logging and/or fix locally and re-push.

7. Test the public website at [https://niceboulderrealty.com](https://niceboulderrealty.com) to confirm everything works correctly.

# More Info

Git is tricky to learn. Here's a [quick reference](https://training.github.com/downloads/github-git-cheat-sheet.pdf) of common commands, or consult [Git's online docs](https://git-scm.com/docs/git#_git_commands) for more advanced features (shouldn't be necessary).

# Credits

This website was created by Chris Russell in February 2023. It uses the following open source tech stack and free content:

* [Github Pages](https://pages.github.com) for hosting the website, version control, issue tracking, and more.
* [Jekyll](https://jekyllrb.com) static site generator for compiling the website.
* [Kramdown](https://kramdown.gettalong.org) for compiling [Markdown](https://en.wikipedia.org/wiki/Markdown) content into HTML.
* [Liquid](https://shopify.github.io/liquid) template language for compiling HTML pages.
* [Jekyll Advance Theme](https://jekyllthemes.io/theme/advance-multi-purpose-theme) as a templated starting point from which to customize and build the website.
* [Bootstrap](https://getbootstrap.com) for responsive web design and interactivity.
* [SASS/SCSS](https://sass-lang.com) for CSS pre-processing.
* [Google Analytics](https://marketingplatform.google.com/about/analytics) for monitoring site activity.
* [WebP](https://developers.google.com/speed/webp) image file format for improved image compression and performance.
* [Font Awesome 5](https://fontawesome.com) icons with [free license](https://fontawesome.com/license/free).
* [Icons8](https://icons8.com) icons with [free license](https://icons8.com/license).
* [Pexels](https://www.pexels.com) free photos with [free license](https://www.pexels.com/license).
* [Unsplash](https://unsplash.com) demo images with [free license](https://unsplash.com/license).
