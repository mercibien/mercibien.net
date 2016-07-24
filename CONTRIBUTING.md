Contributing Changes to MerciBien
---------------------------------

Contribution areas are listed in `AUTHORS.md` and there is an [official list of issues we need external help on][help]. If you have any other idea, feel free to [suggest it on the team channel][team].

Contributing to the project is both welcomed and encouraged. To do so, you have these options:


# Hacking the code directly

## If you are a developper

- fork the project & create a branch for your changes.
- Modify the files as appropriate.
	- if you want to contribute a translation/localization, see below.
- For Python code, make `flake8` happy on your modified files;
	- you can ignore `["E221", "E241", "E272"]`, I do.
	- Please, remove trailing spaces/tabs at the end of *any* line.
-  Update documentation (you can do it via the Django admin for a friendly-editing interface, it's the `Help contents` section) :
	- if you add/change any user-visible feature, update the “features” documentation in english, if not sure of your english, feel free to ask on the IRC channel.
		- If you are not english native, be kind enough to update the translated version in your native language.
		- eventually ping on IRC for other developpers, it's best if we can gather all translations before accepting the patch.
	- If you change anything related to the documented architecture, update it in the `docs/` folder.
- Add tests to the following files and follow their format/conventions:
    - `{base,core}/tests/test_*.py`
-  Obviously, make sure all tests pass. Sorry for having asked it. Just run `make test` and enjoy whatever pleases you.
- Push your branch to `GitHub` and submit a pull request,
- Wait for my neurons to connect.

## If you are not a developper

- just edit the files (documentation, README…), and [ask for any help you need][team].


# Translating or localizing the code

Currently, Merci Bien uses `django-rosetta`, available at your local address [http://localhost:8000/translate/](http://localhost:8000/translate/).

Even english localization is available to translators.

In the code, create i18n strings like “codes”, eg. `exception.article.cannot_set_title`, `info.article.title_changed(%(article_id)s, %(old_title)s, %(new_title)s)`, `label.import_url.urls_list` and so on.

NOTE: **LOGGER calls are not translated**, because they are never shown to the user. Only messages, labels, etc are translated.

Important: **we always use named arguments in i18n strings**, for more translators understanding of translatable strings.
    - Python code examples:

	# translated
    message = _(u'exception.article.cannot_extract_title('
                             u'%(article)s)') % (article=self, )

    # Not translated
    LOGGER.info(u'Changed title of article #%s from %s to %s',
                self.id, old_title, self.title)

    # Translated, in case they reach the user as last chance.
    raise Exception(_(u'Could not create article from url {url}'
                    ).format(url=url))

More examples in Django templates will come as soon as we implement some.


# Writing some documentation

[Reach us on the discussion channels][team] to discuss about missing documentation areas, and get some help / guidance if you ever need some.


# Advocating for the project / web application

[Reach us on the discussion channels][team] to discuss about it first, and get some help / guidance if you ever need some.


# Submitting issues / feedback

If you don't feel comfortable forking the project or modifying it, you can also [submit an issue](https://github.com/mercibien/mercibien.net/issues) that includes the appropriate request.

If you found a bug, please include anything that can help us reproduce it, **excluding any of your passwords**. Never give them to anybody. If we need to access some of your personal data for any reason, we will discuss it first, and ask for something like a read-only/partial-display screen-sharing with your approval.

If you are not a developer and do not feel comfortable with `GitHub`, [Just reach us on the discussion channels][team] to submit ideas and feedback. We (developpers) will do our best to integrate them in our roadmap.

Thanks!


  [team]: http://teams.1flow.net/mercibien/channels/town-square
  [help]: https://github.com/mercibien/mercibien.net/issues?labels=needs+help&page=1&state=open
