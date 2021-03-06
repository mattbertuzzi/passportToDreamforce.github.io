# Passport To Dreamforce

![Passport Image](https://raw.githubusercontent.com/passportToDreamforce/passportToDreamforce.github.io/master/images/twitter_large.png)

This project is a community-sourced and curated list of links/information for international travelers heading to salesforce.com's Dreamforce conference.

# Contributor Guide
## Structure
The site is generated by using [Jeykll](https://jekyllrb.com/) and the whole site is data driven using [YAML](http://yaml.org/).  Let's take a look at where the data lives and how it is structured

### [site.yml](https://github.com/passportToDreamforce/passportToDreamforce.github.io/blob/master/_data/site.yml)
This file is the driving force behind the entire site.  The sections should be pretty self explanatory but let's take a look at how we handle translations

```yml
maintitle:
    en: Passport to Dreamforce
```

The first line of `maintitle` is our key and the second line is our lookup to the page's language.  By default we use `en` but to add a new translations, simply add a new line with the [ISO 639-1 Code](https://www.loc.gov/standards/iso639-2/php/code_list.php) in front.  For example, to add a Spanish translation, our YAML will look like


```yml
maintitle:
    en: Passport to Dreamforce
    es: Pasaporte a Dreamforce
```

Most of the rest of this file are just copy text for the rest of the site.  The only real exception being `sections` and `langs`.  These are lists of data that look up into other YAML files.  For example, the `sections` has a list of sections that get rendered on the page.  This data is pulled from a YAML file with the same name.

### [langs.yml](https://github.com/passportToDreamforce/passportToDreamforce.github.io/blob/master/_data/langs.yml)
This file contains mapping for languages to the name and links.  This is rendered on the page under the gear icon.

### section.yml
Each section has it's own YAML file that contains two root elements

#### title
This are the translations for each language for the section title

#### links
This is a list of links to be displayed in the section.  Each link contains a `name` `url` and `desc`

If you want to have a description with multiple lines or HTML formatting this is supported.  But it does require special markup

```yml
links:
    - en:
        name: Example Link
        url: http://example.com
        desc: |
            <p>Some HTML goes here</p>
             <p>This can have multiple lines, you just have to have a space before</p>
```

## Contributing
If you've never worked with github, please read over [Working with forks](https://help.github.com/articles/working-with-forks/) and [Creating a pull request from a fork](https://help.github.com/articles/creating-a-pull-request-from-a-fork/).

Once you have an update, please submit a pull request and the team will review it and merge it in.

### New Links
The simplest way to contribute is to add new links.

Please keep the following in mind

 * Try to use official government sites where possible.
 * Provide a concise description of the link but don't make it too short

### Translations
We are always looking for people willing to translate links.

#### New Language
If you do not see your language on the site you will need to do a little bit of base work to get it started.

1. Copy `index_es.html` to `index_XX.html` using the ISO code
2. Edit `index_XX.html` to have the ISO code under `lang` and `permalink`
3. Edit `_data/site.yml` and add the ISO code under `langs` and add translations for each section
4. Edit `_data/langs.yml` and add the a new stanza for the language

#### Links
Find a link that has not been translated and add the translations under the link.

```yml
     - en:
          name: Visitor Visa
          url: https://travel.state.gov/content/visas/en/visit/visitor.html
          desc: "Learn about visa category B-1: attending a scientific, educational, professional, or business conference."
       es:
          name: Visa de turista
          url: https://travel.state.gov/content/visas/en/visit/visitor.html
          desc: "Aprenda sobre la categoría de visa B-1: asistir a una conferencia científica, educativa, profesional o de negocios."
```

_NOTE: There is **NOT** a hyphen (`-`) in front of the translation.  There is only a hyphen in front of each new link_