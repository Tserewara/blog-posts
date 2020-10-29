# My third post

```py
import markdown
from flask import Flask
import markdown.extensions.fenced_code
import markdown.extensions.codehilite
from pygments.formatters import HtmlFormatter
from fetch_github import get_article_from_github
from html_generator import generate_html

app = Flask(__name__)

@app.route("/<path:path_to_article>")
def index(path_to_article):
    article = get_article_from_github(path_to_article)

    md_template_string = markdown.markdown(
        article,
        extensions=["fenced_code", "codehilite"]
    )

    formatter = HtmlFormatter(style="dracula", full=True, cssclass="codehilite")
    css_string = formatter.get_style_defs()
    md_css_string = f"<style>{css_string + add_styles}</style>"

    md_template = md_css_string + md_template_string

    return generate_html(md_template)


if __name__ == "__main__":
    app.run(debug=True)

```