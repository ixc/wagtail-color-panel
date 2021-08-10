This is a fork of https://github.com/marteinn/wagtail-color-panel, to fix a bug brought about in Wagtail 2.13 where the colour input of the  `ColorInputWidget` isn't updated on initial render, while the text input is.

Note that the current fix has a delay of about half a second where the `DomContentLoaded` event fetches the pre-rendered colour code from the text input. \
A think a full fix would require a widget adapter to be set up so that the Wagtail Telepath library knows to render both the text AND colour input.

More info here: https://docs.wagtail.io/en/stable/advanced_topics/customisation/streamfield_blocks.html#custom-streamfield-blocks,
and here: https://docs.wagtail.io/en/latest/reference/streamfield/widget_api.html#streamfield-widget-api.

And an example of converting a streamfield widget (library) to be Wagtail 2.13 ready can be found in `django-instance-selector`: https://github.com/ixc/wagtail-instance-selector/pull/14.

*Original docs are listed below.*

<br><hr><br>

![Wagtail-Color-Panel](https://github.com/marteinn/wagtail-color-panel/workflows/Wagtail-Color-Panel/badge.svg)
[![PyPI version](https://badge.fury.io/py/wagtail-color-panel.svg)](https://badge.fury.io/py/wagtail-color-panel)

# Wagtail-Color-Panel

Introduces panels for selecting colors in Wagtail.

![Screen1](https://raw.githubusercontent.com/marteinn/wagtail-color-panel/develop/img/img-in-streamfield.png)


## Features

- NativeColorPanel that can be used in your edit handler
- NativeColorBlock for usage in a StreamField
- Based on the native HTML5 color picker
- A custom db field for improved validation
- PolyfillColorPanel for cases that require IE11 support (built on [Spectrum](https://github.com/bgrins/spectrum))


## Example

```python
from wagtail.core.models import Page

from wagtail_color_panel.fields import ColorField
from wagtail_color_panel.edit_handlers import NativeColorPanel


class MyPage(Page):
    color = ColorField()

    content_panels = Page.content_panels + [
        NativeColorPanel('color'),
    ]
```


## Documentation

- [Getting started](./docs/1_getting_started.md)
- [Adding panel to a Page](./docs/2_adding_to_a_page.md)
- [Adding to a StreamField](./docs/3_adding_to_a_streamfield.md)
- [Reference](./docs/4_reference.md)

## Contributing

Want to contribute? Awesome. Just send a pull request.


## License

Wagtail-Color-Panel is released under the [MIT License](http://www.opensource.org/licenses/MIT).
