# Otree docs & notes
### 2019 Spring semester, notes for research assistant

[Otree Docs](https://otree.readthedocs.io/)

## Timeouts: 

#### timeout_seconds
To set a time limit on your page, add timeout_seconds like this:

```python
class Page1(Page):
    timeout_seconds = 60
```

After the time runs out, the page auto-submits.

#### timeout_happened
This attribute is automatically set to True if the page was submitted by timeout. It can be accessed in before_next_page. For example:

```python
class Page1(Page):
    timeout_seconds = 60

    def before_next_page(self):
        if self.timeout_happened:
            self.player.my_random_variable = random.random()
```

timeout_happened is undefined in other methods like vars_for_template, because the timeout countdown only starts after the page is rendered.
Here is were we can specify default values or try to claculate the best guess for player-submitted value. 

## Dynamic page timeout

can be done through: 
`get_timeout_seconds`
This is a dynamic alternative to timeout_seconds, so that you can base the timeout on self.player, self.session, etc... Would be set in SESSION_CONFIGS rather than pages.py. Then in pages.py:

```python
class MyPage(Page):

    def get_timeout_seconds(self):
        return self.session.config['my_page_timeout_seconds']
```