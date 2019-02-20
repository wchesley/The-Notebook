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

## Custom HTML Pages: 

#### Raw HTML example: custom user interface with JavaScript
Let’s say you don’t want users to fill out form fields, but instead interact with some sort of visual app, like a clicking on a chart or playing a graphical game. Or, you want to record extra data like how long they spent on part of the page, how many times they clicked, etc.

You can build these interfaces in any front-end framework you want. Simple ones can be done with jQuery; more complex ones would use something like React or Polymer.

Then, use JavaScript to record the relevant data points and store it in a form field. For example: (Does not have to be a hidden field)

```python
# models.py
my_hidden_input = models.IntegerField()

# pages.py
form_fields = ['my_hidden_input']

# HTML template
<input type="hidden" name="my_hidden_input" id="id_my_hidden_input"/>
```
Then you can use JavaScript to set the value of that input, by selecting the element by id `id_my_hidden_input`, and setting its value attribute.

When the page is submitted, the value of your hidden input will be recorded in oTree like any other form field.

### Remember!

To use raw HTML, just ensure that each field in your Page’s form_fields has a corresponding `<input>` element with a matching name attribute.

Remember that for any field `my_field`, you should include `{{ form.my_field.errors }}`, so that if there is an error in the form, the participant will see the error message.