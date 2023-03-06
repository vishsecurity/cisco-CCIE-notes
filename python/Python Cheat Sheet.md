# Python Cheat Sheet

Python is an interpreted, high-level, general-purpose programming language. **Python Cheat Sheet** tries to provide a basic reference for beginner and advanced developers, lower the entry barrier for newcomers, and help veterans refresh the old tricks.

## [Pygame: Eendering The Text Cheat Sheet](https://simplecheatsheet.com/pygame-rendering-the-text/)

You can use text for a variety of purposes in a game. For example you can share information with players, and you can display a score.

### Displaying a message

The following code defines a message, then a color for the text and the background color for the message. A font is defined using the default system font, with a font size of 48. The font.render() function is used to create an image of the message, and we get the rect object associated with the image. We then center the image on the screen and display it.

```
msg = "Play again?"
msg_color = (100, 100, 100)
bg_color = (230, 230, 230)
f = pg.font.SysFont(None, 48)
msg_image = f.render(msg, True, msg_color,bg_color)
msg_image_rect = msg_image.get_rect()
msg_image_rect.center = screen_rect.center
screen.blit(msg_image, msg_image_rect)
```

## [Pygame: Detecting Collisions Cheat Sheet](https://simplecheatsheet.com/pygame-detecting-collisions/)

You can detect when a single object collides with any member of a group. You can also detect when any member of one group collides with a member of another group.

### Collisions between a single object and a group

The spritecollideany() function takes an object and a group, and returns True if the object overlaps with any member of the group

```
if pg.sprite.spritecollideany(ship, aliens):
    ships_left -= 1
```

### Collisions between two groups

The sprite.groupcollide() function takes two groups, and two booleans. The function returns a dictionary containing information about the members that have collided. The booleans tell Pygame whether to delete the members of either group that have collided.

```
collisions = pg.sprite.groupcollide(bullets, aliens, True, True)
score += len(collisions) * alien_point_value
```

## [Pygame: Groups Cheat Sheet](https://simplecheatsheet.com/pygame-groups/)

Pygame has a Group class which makes working with a group of similar objects easier. A group is like a list, with some extra functionality that’s helpful when building games

### Making and filling a group

An object that will be placed in a group must inherit from Sprite.

```
from pygame.sprite import Sprite, Group

def Bullet(Sprite):
    ...
    def draw_bullet(self):
    ...
    def update(self):
    ...
bullets = Group()
new_bullet = Bullet()
bullets.add(new_bullet)
```

### Looping through the items in a group

The sprites() method returns all the members of a group

```
for bullet in bullets.sprites():
     bullet.draw_bullet()
```

### Calling update() on a group

Calling update() on a group automatically calls update() on each member of the group

```
bullets.update()
```

### Removing an item from a group

It’s important to delete elements that will never appear again in the game, so you don’t waste memory and resources.

```
bullets.remove(bullet)
```

## [Pygame: Responding to the mouse event Cheat Sheet](https://simplecheatsheet.com/pygame-responding-to-the-mouse-event/)

Pygame’s event loop registers an event any time the mouse moves, or a mouse button is pressed or released.

### Responding to the mouse button

```
for event in pg.event.get():
    if event.type == pg.MOUSEBUTTONDOWN:
        ship.fire_bullet()
```

### Finding the mouse position

The mouse position is returned as a tuple

```
mouse_pos = pg.mouse.get_pos()
```

### Clicking a button

You might want to know if the cursor is over an object such as a button. The rect.collidepoint() method returns true when a point is inside a rect object.

```
if button_rect.collidepoint(mouse_pos):
     start_game()
```

### Hiding the mouse

```
pg.mouse.set_visible(False)
```

## [Working with Images in Pygame](https://simplecheatsheet.com/working-with-images-in-pygame/)

Loading an image

```
ship = pg.image.load('images/ship.bmp')
```

Getting the rect object from an image

```
ship_rect = ship.get_rect
```

### Positioning an image

With rects, it’s easy to position an image wherever you want on the screen, or in relation to another object. The following code positions a ship object at the bottom center of the screen.

```
ship_rect.midbottom = screen_rect.midbottom
```

### Drawing an image to the screen

Once an image is loaded and positioned, you can draw it to the screen with the blit() method. The blit() method acts on the screen object, and takes the image object and image rect as arguments.

```
# Draw ship to screen. 
screen.blit(ship, ship_rect)
```

### The blitme() method

Game objects such as ships are often written as classes. Then a blitme() method is usually defined, which draws the object to the screen.

```
def blitme(self):
    """Draw ship at current location."""
    self.screen.blit(self.image, self.rect)
```

## [Python: Lists Cheat Sheet](https://simplecheatsheet.com/python-lists/)

A list stores a series of items in a particular order. Lists allow you to store sets of information in one place, whether you have just a few items or millions of items. Lists are one of Python’s most powerful features readily accessible to new programmers, and they tie together many important concepts in programming.

### Defining a list

Use square brackets to define a list, and use commas to separate individual items in the list. Use plural names for lists, to make your code easier to read.

**Making a list**

```
users = ['val', 'bob', 'mia', 'ron', 'ned']
```

### Accessing Elements

Individual elements in a list are accessed according to their position, called the index. The index of the first element is 0, the index of the second element is 1, and so forth. Negative indices refer to items at the end of the list. To get a particular element, write the name of the list and then the index of the element in square brackets.

Getting the first element

```
first_user = users[0]
```

Getting the second element

```
second_user = users[1]
```

Getting the last element

```
newest_user = users[-1]
```

### Modifying individual items

Once you’ve defined a list, you can change individual elements in the list. You do this by referring to the index of the item you want to modify.

Changing an element

```
users[0] = 'valerie'
users[-2] = 'ronald'
```

### Adding element

You can add elements to the end of a list, or you can insert
them wherever you like in a list.

Adding an element to the end of the list

```
users.append('amy')
```

Starting with an empty list

```
users = []
users.append('val')
users.append('bob')
users.append('mia')
```

Inserting elements at a particular position

```
users.insert(0, 'joe')
users.insert(3, 'bea')
```

### Removing Element

You can remove elements by their position in a list, or by the value of the item. If you remove an item by its value, Python removes only the first item that has that value.

Deleting an element by its position

```
del users[-1] 
```

Removing an item by its value

```
users.remove('mia')
```

### Popping Elements

If you want to work with an element that you’re removing from the list, you can “pop” the element. If you think of the list as a stack of items, pop() takes an item off the top of the stack. By default pop() returns the last element in the list, but you can also pop elements from any position in the list.

Pop the last item from a list

```
most_recent_user = users.pop()
print(most_recent_user)
```

Pop the first item in a list

```
first_user = users.pop(0)
print(first_user)
```

### Get length of a list

The len() function returns the number of items in a list.

**Find the length of a list**

```
num_users = len(users)
print("We have " + str(num_users) + " users.")
```

### Sorting a list

The sort() method changes the order of a list permanently. The sorted() function returns a copy of the list, leaving the original list unchanged. You can sort the items in a list in alphabetical order, or reverse alphabetical order. You can also reverse the original order of the list. Keep in mind that lowercase and uppercase letters may affect the sort order.

**Sorting a list permanently**

```
users.sort()
```

**Sorting a list permanently in reverse alphabetical order**

```
users.sort(reverse=True)
```

**Sorting a list temporarily**

```
print(sorted(users))
print(sorted(users, reverse=True))
```

**Reversing the order of a list**

```
users.reverse()
```

### Looping through the list

Lists can contain millions of items, so Python provides an efficient way to loop through all the items in a list. When you set up a loop, Python pulls each item from the list one at a time and stores it in a temporary variable, which you provide a name for. This name should be the singular version of the list name.

The indented block of code makes up the body of the loop, where you can work with each individual item. Any lines that are not indented run after the loop is completed.

**Printing all items in a list**

```
for user in users:
    print(user)
```

**Printing a message for each item, and a separate message afterward**

```
for user in users:
    print("Welcome, " + user + "!")
    print("Welcome, we're glad to see you all!")
```

### Looping the range of number

You can use the range() function to work with a set of numbers efficiently. The range() function starts at 0 by default and stops one number below the number passed to it. You can use the list() function to efficiently generate a large list of numbers.

Printing the numbers 0 to 1000

```
for number in range(1001):
print(number)
```

Printing the numbers 1 to 1000

```
for number in range(1, 1001):
print(number)
```

Making a list of numbers from 1 to a million

```
numbers = list(range(1, 1000001))
```

### Simple Statistic

There are a number of simple statistics you can run on a list containing numerical data.

Finding the minimum value in a list

```
ages = [93, 99, 66, 17, 85, 1, 35, 82, 2, 77]
youngest = min(ages)
```

Finding the maximum value

```
ages = [93, 99, 66, 17, 85, 1, 35, 82, 2, 77]
oldest = max(ages)
```

Finding the sum of all values

```
ages = [93, 99, 66, 17, 85, 1, 35, 82, 2, 77]
total_years = sum(ages)
```

### Slicing a list

You can work with any set of elements from a list. A portion of a list is called a slice. To slice a list start with the index of the first item you want, then add a colon and the index after the last item you want. Leave off the first index to start at the beginning of the list, and leave off the last index to slice through the end of the list.

Getting the first three items

```
finishers = ['kai', 'abe', 'ada', 'gus', 'zoe']
first_three = finishers[:3]
```

Getting the middle three items

```
middle_three = finishers[1:4]
```

Getting the last three items

```
last_three = finishers[-3:]
```

### Copying a list in python

To copy a list make a slice that starts at the first item and ends at the last item. If you try to copy a list without using this approach, whatever you do to the copied list will affect the original list as well.

Making a copy of a list

```
finishers = ['kai', 'abe', 'ada', 'gus', 'zoe']
copy_of_finishers = finishers[:]
```

### Python list comprehensions

You can use a loop to generate a list based on a range of numbers or on another list. This is a common operation, so Python offers a more efficient way to do it. List comprehensions may look complicated at first; if so, use the for loop approach until you’re ready to start using comprehensions.

To write a comprehension, define an expression for the values you want to store in the list. Then write a for loop to generate input values needed to make the list.

Using a loop to generate a list of square numbers

```
squares = []
for x in range(1, 11):
     square = x**2
     squares.append(square)
```

Using a comprehension to generate a list of square numbers

```
squares = [x**2 for x in range(1, 11)]
```

Using a loop to convert a list of names to upper case

```
names = ['kai', 'abe', 'ada', 'gus', 'zoe']
upper_names = []
for name in names:
     upper_names.append(name.upper())
```

Using a comprehension to convert a list of names to upper case

```
names = ['kai', 'abe', 'ada', 'gus', 'zoe']
upper_names = [name.upper() for name in names]
```

### Python Tuples

A tuple is like a list, except you can’t change the values in a tuple once it’s defined. Tuples are good for storing information that shouldn’t be changed throughout the life of a program. Tuples are designated by parentheses instead of square brackets. (You can overwrite an entire tuple, but you can’t change the individual elements in a tuple.)

Defining a tuple

```
dimensions = (800, 600)
```

Looping through a tuple

```
for dimension in dimensions:
      print(dimension)
```

Overwriting a tuple

```
dimensions = (800, 600)
print(dimensions)
dimensions = (1200, 900)
```

## [Oygame: React Objects Cheat Sheet](https://simplecheatsheet.com/oygame-react-objects/)

Many objects in a game can be treated as simple rectangles, rather than their actual shape. This simplifies code without noticeably affecting game play. Pygame has a rect object that makes it easy to work with game objects.

### Getting the screen rect object

We already have a screen object; we can easily access the rect object associated with the screen.

```
screen_rect = screen.get_rect()
```

### Finding the center of the screen

Rect objects have a center attribute which stores the center point.

```
screen_center = screen_rect.center
```

### Useful rect attributes

Once you have a rect object, there are a number of attributes that
are useful when positioning objects and detecting relative positions
of objects. (You can find more attributes in the Pygame
documentation.)

```
#Individual x and y values:
screen_rect.left, screen_rect.right
screen_rect.top, screen_rect.bottom
screen_rect.centerx, screen_rect.centery
screen_rect.width, screen_rect.height
# Tuples
screen_rect.center
screen_rect.size
```

### Creating a rect object

You can create a rect object from scratch. For example a small rect object that’s filled in can represent a bullet in a game. The Rect() class takes the coordinates of the upper left corner, and the width and height of the rect. The draw.rect() function takes a screen object, a color, and a rect. This function fills the given rect with the given color.

```
bullet_rect = pg.Rect(100, 100, 3, 15)
color = (100, 100, 100)
pg.draw.rect(screen, color, bullet_rect)
```

## [Start a game with pygame](https://simplecheatsheet.com/start-a-game-with-pygame/)

The following code sets up an empty game window, and starts an event loop and a loop that continually refreshes the screen.

### An empty game window

```
import sys
import pygame as pg
def run_game():
    # Initialize and set up screen.
    pg.init()
    screen = pg.display.set_mode((1200, 800))
    pg.display.set_caption("Alien Invasion")

    # Start main loop.
    while True:
        # Start event loop.
        for event in pg.event.get():
            if event.type == pg.QUIT:
                sys.exit()

        # Refresh screen.
        pg.display.flip()

run_game()
```

### Setting a custom window size

The display.set_mode() function accepts a tuple that defines the
screen size.

```
screen_dim = (1200, 800)
screen = pg.display.set_mode(screen_dim)
```

### Setting a custom background-color

Colors are defined as a tuple of red, green, and blue values. Each value ranges from 0-255.

```
bg_color = (230, 230, 230)
screen.fill(bg_color)
```

## [Installing Pygame](https://simplecheatsheet.com/installing-pygame/)

Pygame runs on all systems, but setup is slightly different on each OS. The instructions here assume you’re using Python 3, and provide a minimal installation of Pygame. If these instructions don’t work for your system, see the more detailed notes at http://ehmatthes.github.io/pcc/.

### Install Pygame on Linux

```
sudo apt-get install python3-dev mercurial libsdl-image1.2-dev libsdl2-dev libsdl-ttf2.0-dev
pip install --user hg+http://bitbucket.org/pygame/pygame
```

### Pygame on OS X

This assumes you’ve used Homebrew to install Python 3.

```
brew install hg sdl sdl_image sdl_ttf
pip install --user hg+http://bitbucket.org/pygame/pygame
```

### Pygame on Windows

Find an installer at https://bitbucket.org/pygame/pygame/downloads/ or http://www.lfd.uci.edu/~gohlke/pythonlibs/#pygame that matches your version of Python. Run the installer file if it’s a .exe or .msi file. If it’s a .whl file, use pip to install Pygame:

```
python –m pip install --user pygame-1.9.2a0-cp35-none-win32.whl
```

### Testing your installation

To test your installation, open a terminal session and try to import
Pygame. If you don’t get any error messages, your installation was
successful.

```
$ python
import pygame
```

## [Django: Create Project](https://simplecheatsheet.com/django-create-project/)

To start a project we’ll create a new project, create a database, and start a development server.

### Create a new project

```
django-admin.py startproject learning_log .
```

### Create a database

```
python manage.py migrate
```

### View the project.

After issuing this command, you can view the project at `http://localhost:8000/`.

```
python manage.py runserver
```

### Create a new app

A Django project is made up of one or more apps.

```
python manage.py startapp learning_logs
```

## [Django: Template Inheritance Cheat Sheet](https://simplecheatsheet.com/django-template-inheritance/)

Many elements of a web page are repeated on every page in the site, or every page in a section of the site. By writing one parent template for the site, and one for each section, you can easily modify the look and feel of your entire site

### The parent template

The parent template defines the elements common to a set of pages, and defines blocks that will be filled by individual pages.

```
<p>
 <a href="{% url 'learning_logs:index' %}">
 Learning Log
 </a>
</p>
{% block content %}{% endblock content %}
```

### The child template

The child template uses the {% extends %} template tag to pull in the structure of the parent template. It then defines the content for any blocks defined in the parent template.

```
{% extends 'learning_logs/base.html' %}
{% block content %}
 <p>
 Learning Log helps you keep track
 of your learning, for any topic you're
 learning about.
 </p>
{% endblock content %}
```

## [Install Django Rest Framework](https://simplecheatsheet.com/install-django-rest-framework/)

Install the package via `pip`:

```
$ pip install djangorestframework
```

Then, add `'rest_framework'` to `INSTALLED_APPS` in your `settings.py` file.

```
INSTALLED_APPS = [
    # Rest of your installed apps ...
    'rest_framework',
]
```

## [Django: Shell Cheat Sheet](https://simplecheatsheet.com/using-django-shell/)

Start a shell session

```
python manage.py shell
```

Access data from the project

```
from learning_logs.models import Topic

Topic.objects.all()
topic = Topic.objects.get(id=1)
topic.text 'Chess'
```

## [Django: Rest Framework Serialization Cheat Sheet](https://simplecheatsheet.com/django-rest-framework-serialization/)

Serializers allow complex data like querysets and model instances to be converted to native Python datatypes that can then be easily rendered into JSON, XML, and other formats.

### Using ModelSerializer class:

Suppose we wanted to create a PostSerializer for our example Post model and CommentSerializer for our Comment model.

```
class PostSerializer(serializers.ModelSerializer):

    class Meta:
        model = Post
        fields = ('id', 'title', 'text', 'created')
        
        
class CommentSerializer(serializers.ModelSerializer):

    class Meta:
        model = Comment
        fields = ('post', 'user', 'text')
```

Or also you could use `exclude` to exclude certain fields from being seialized. ModelSerializer has default implementations for the `create()` and `update()` methods.

#### Nested Serialization

By default, instances are serialized with primary keys to represent relationships. To get nested serialization we could use, *General* or *Explicit* methods.

**General**

Using `depth` parameter.

```
class CommentSerializer(serializers.ModelSerializer):

    class Meta:
        model = Comment
        fields = '__all__'
        depth = 2
```

**Explicit**

Yuo can also define and nest serializers within eachother…

```
class CommentSerializer(serializers.ModelSerializer):
    post = PostSerializer()
    
    class Meta:
        model = Comment
        fields = '__all__'
```

So here, the comment’s `post` field (how we named it in models.py) will serialize however we defined it in `PostSerializer`.

### HyperlinkedModelSerializer

This makes your web API a lot more easy to use (in browser) and would be a nice feature to add.

Let’s say we wanted to see the comments that every post has in each of the Post instances of our API.

With `HyperlinkedModelSerializer`, instead of having nested primary keys or nested fields, we get a link to each individual Comment (URL).

```
class PostSerializer(serializers.HyperlinkedModelSerializer):

    class Meta:
        model = Post
        fields = ('id', 'title', 'text', 'created', 'comments')
        read_only_fields = ('comments',)
```

**Note:** without the `read_only_fields`, the `create` form for Posts would always require a `comments` input, which doesn’t make sense (comments on a post are normally made AFTER the post is created).

Another way of hyperlinking is just adding a `HyperlinkedRelatedField` definition to a normal serializer.

```
class PostSerializer(serializers.ModelSerializer):
    comments = serializers.HyperlinkedRelatedField(many=True, view_name='comment-detail', read_only=True)
    
    class Meta:
        model = Post
        fields = ('id', 'title', 'text', 'created', 'comments')
```

### Dynamically modifying fields in the serializer

This makes your web API a lot more easy for extract limited number of parameter in response. Let’s say you want to set which fields should be used by a serializer at the point of initialization.

Just copy below code and past it in your serliazer file

```
class DynamicFieldsModelSerializer(serializers.ModelSerializer):

    def __init__(self, *args, **kwargs):
        # Don't pass the 'fields' arg up to the superclass
        fields = kwargs.pop('fields', None)

        # Instantiate the superclass normally
        super(DynamicFieldsModelSerializer, self).__init__(*args, **kwargs)

        if fields is not None:
            # Drop any fields that are not specified in the `fields` argument.
            allowed = set(fields)
            existing = set(self.fields.keys())
            for field_name in existing - allowed:
                self.fields.pop(field_name)
```

Extend `DynamicFieldsModelSerializer` from your serializer class

```
class UserSerializer(DynamicFieldsModelSerializer):
    class Meta:
        model = User
        fields = ('id', 'username', 'email')
```

Mention the fields name inside `fields`

```
UserSerializer(user, fields=('id', 'email'))
```

Here, you will get only `id` and `email` from serializer instead of all.

## [DjangoL Passing Data into Viet Cheat Sheet](https://simplecheatsheet.com/django-passing-data-into-viet/)

Most pages in a project need to present data that are specific to the current user.

### URL parameters

A URL often needs to accept a parameter telling it which data to access from the database. The second URL pattern shown here looks for the ID of a specific topic and stores it in the parameter topic_id.

```
urlpatterns = [
    url(r'^$', views.index, name='index'),
    url(r'^topics/(?P<topic_id>\d+)/$',
    views.topic, name='topic'),
]
```

### Using data in a view

The view uses a parameter from the URL to pull the correct data from the database. In this example the view is sending a context dictionary to the template, containing data that should be displayed on the page.

```
def topic(request, topic_id):
    """Show a topic and all its entries."""
    topic = Topics.objects.get(id=topic_id)
    entries = topic.entry_set.order_by('-date_added')
    context = {
        'topic': topic,
        'entries': entries,
    }
    return render(request, 'learning_logs/topic.html', context)
```

### Using data in a template

The data in the view function’s context dictionary is available within the template. This data is accessed using template variables, which are indicated by doubled curly braces. The vertical line after a template variable indicates a filter. In this case a filter called date formats date objects, and the filter linebreaks renders paragraphs properly on a web page.

```
{% extends 'learning_logs/base.html' %}
{% block content %}
    <p>Topic: {{ topic }}</p>
    <p>Entries:</p>
    <ul>
    {% for entry in entries %}
        <li>
            <p>{{ entry.date_added|date:'M d, Y H:i' }}</p>
            <p>{{ entry.text|linebreaks }}</p>
        </li>
        {% empty %}
        <li>There are no entries yet.</li>
        {% endfor %}
    </ul>
{% endblock content %}
```

## [Django: Rest Framework Views Cheat Sheet](https://simplecheatsheet.com/django-rest-framework-views/)

There are many options for creating views for your web API, it really depends on what you want and personal preference.

### Using Function-based views:

```
from rest_framework.decorators import api_view
from rest_framework.response import Response
from rest_framework.parsers import JSONParser
from rest_framework import status
from posts.models import Post
from posts.serializers import PostSerializer

@api_view(['GET', 'POST'])
def post_list(request, format=None):

    if request.method == 'GET':
        posts = Post.objects.all()
        serializer = PostSerializer(posts, many=True)
        return Response(serializer.data)

    elif request.method == 'POST':
        data = JSONParser().parse(request)
        serializer = PostSerializer(data=data)

        if serializer.is_valid():
            serializer.save()
            return Response(serializer.data, status=status.HTTP_201_CREATED)
        return Response(serializer.errors, status=status.HTTP_400_BAD_REQUEST)
```

### Using Class-based views:

```
from rest_framework.response import Response
from rest_framework import status
from rest_framework.views import APIView
from posts.models import Post
from posts.serializers import PostSerializer


class PostList(APIView):
    def get(self, request, format=None):
        snippets = Post.objects.all()
        serializer = PostSerializer(snippets, many=True)
        return Response(serializer.data)

    def post(self, request, format=None):
        serializer = PostSerializer(data=request.data)
        if serializer.is_valid():
            serializer.save()
            return Response(serializer.data, status=status.HTTP_201_CREATED)

        return Response(serializer.errors, status=status.HTTP_400_BAD_REQUEST)
```

### Using Generic Class-based views:

```
from rest_framework import generics
from posts.models import Post
from posts.serializers import PostSerializer


class PostList(generics.ListCreateAPIView):
    queryset = Post.objects.all()
    serializer_class = PostSerializer
```

### Using Mixins:

```
from rest_framework import generics, mixins
from posts.models import Post
from posts.serializers import PostSerializer


class PostList(generics.GenericAPIView,
               mixins.ListModelMixin,
               mixins.CreateModelMixin
               ):
    queryset = Post.objects.all()
    serializer_class = PostSerializer

    def get(self, request, *args, **kwargs):
        return self.list(request, *args, **kwargs)

    def post(self, request, *args, **kwargs):
        return self.create(request, *args, **kwargs)
```

### Using ViewSets:

With `ModelViewSet` (in this case), you don’t have to create separate views for getting list of objects and detail of one object. ViewSet will handle it for you in a consistent way for both methods.

```
from rest_framework import viewsets
from posts.models import Post
from posts.serializers import PostSerializer


class PostViewSet(viewsets.ModelViewSet):
    """
    A viewset for viewing and editing post instances.
    """
    queryset = Post.objects.all()
    serializer_class = PostSerializer
```

#### Routers

Routers in ViewSets allow the URL configuration for your API to be automatically generated using naming standards.

```
from rest_framework.routers import DefaultRouter
from posts.views import PostViewSet

router = DefaultRouter()
router.register(r'users', UserViewSet)
urlpatterns = router.urls
```

#### Custom Actions in ViewSets

DRF provides helpers to add custom actions for *ad-hoc* behaviours with the `@action` decorator. The router will configure its url accordingly. For example, we can add a `comments` action in the our `PostViewSet` to retrieve all the comments of a specific post as follows:

```
from rest_framework import viewsets
from rest_framework.decorators import action
from posts.models import Post
from posts.serializers import PostSerializer, CommentSerializer


class PostViewSet(viewsets.ModelViewSet):
   ...
   
   @action(methods=['get'], detail=True)
   def comments(self, request, pk=None):
       try:
           post = Post.objects.get(id=pk)
       except Post.DoesNotExist:
           return Response({"error": "Post not found."},
                           status=status.HTTP_400_BAD_REQUEST)
       comments = post.comments.all()
       return Response(CommentSerializer(comments, many=True))
```

Upon registering the view as `router.register(r'posts', PostViewSet)`, this action will then be available at the url `posts/{pk}/comments/`.

## [Django: Building a Page Cheat Sheet](https://simplecheatsheet.com/django-building-a-page/)

Users interact with a project through web pages, and a project’s home page can start out as a simple page with no data. A page usually needs a URL, a view, and a template.

### Mapping a project’s URLs

The project’s main urls.py file tells Django where to find the urls.py
files associated with each app in the project.

```
from django.conf.urls import include, url
from django.contrib import admin

urlpatterns = [
    url(r'^admin/', include(admin.site.urls)),
    url(r'', include('learning_logs.urls', namespace='learning_logs')),
]
```

### Mapping an app’s URLs

An app’s urls.py file tells Django which view to use for each URL in
the app. You’ll need to make this file yourself, and save it in the
app’s folder.

```
from django.conf.urls import url
from . import views

urlpatterns = [
    url(r'^$', views.index, name='index'),
]
```

### Writing a simple view

A view takes information from a request and sends data to the browser, often through a template. View functions are stored in an app’s views.py file. This simple view function doesn’t pull in any data, but it uses the template index.html to render the home page. from django.shortcuts import render

```
def index(request):
    """The home page for Learning Log."""
    return render(request, 'learning_logs/index.html')
```

### Writing a simple template

A template sets up the structure for a page. It’s a mix of html and template code, which is like Python but not as powerful. Make a folder called templates inside the project folder. Inside the templates folder make another folder with the same name as the app. This is where the template files should be saved.

```
<p>Learning Log</p>
<p>Learning Log helps you keep track of your
learning, for any topic you're learning
about.</p>
```

## [Working with Django Models](https://simplecheatsheet.com/working-with-django-models/)

### Defining a model

To define the models for your app, modify the file models.py that was created in your app’s folder. The **str**() method tells Django how to represent data objects based on this model.

```
from django.db import models

"""A topic the user is learning about."""
class Topic(models.Model):
    text = models.CharField(max_length=200)
    date_added = models.DateTimeField(
    auto_now_add=True)

    def str(self):
         return self.text
```

### Defining a model with a foreign key

```
class Entry(models.Model):
    """Learning log entries for a topic."""
    topic = models.ForeignKey(Topic)
    text = models.TextField()
    date_added = models.DateTimeField(
    auto_now_add=True)
    def str(self):
        return self.text[:50] + "…"
```

### Activating a model

To use a model the app must be added to the tuple `INSTALLED_APPS`, which is stored in the project’s settings.py file

```
INSTALLED_APPS = (
    --snip--
    'django.contrib.staticfiles',
    # My apps
    'learning_logs',
)
```

### Migrating the database

The database needs to be modified to store the kind of data that the model represents.

```
python manage.py makemigrations learning_logs
python manage.py migrate
```

### Creating a superuser

A superuser is a user account that has access to all aspects of the project.

```
python manage.py createsuperuser
```

### Registering a model

You can register your models with Django’s admin site, which
makes it easier to work with the data in your project. To do this,
modify the app’s admin.py file.

```
from django.contrib import admin
from learning_logs.models import Topic
admin.site.register(Topic)
```

## [Install Django](https://simplecheatsheet.com/install-django/)

It’s usually best to install Django to a virtual environment, where your project can be isolated from your other Python projects. Most commands assume you’re working in an active virtual environment.

Create a virtual environment

```
$ python –m venv v
```

Activate the environment (Linux and OS X)

```
$ source v/bin/activate
```

Activate the environment (Windows)

```
venv\Scripts\activate
```

Install Django to the active environment

```
(venv)$ pip install Django
```
