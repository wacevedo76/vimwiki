[[--------------------------------------------------------------------------------]]
= Django (Python MVC Webapp framework) =
--------------------------------------------------------------------------------
= Features =
* The admin site
* Object-relational mapper (ORM)
* Authentication
* Caching
--------------------------------------------------------------------------------
== Common commands ==
  start Django project       | django-admin.py startproject <name of project>
  Start new Django app       | python manage.py startapp <app name> . <--
                             |  the period makes current directory project dir
                             | * don't forget to register the new app in settins
                             |   INSTALLED_APPS
  Start server               | python manage.py runserver  <-- default is 8000
  Runnng unit tests          | python manage.py test
  Run migration              | python manage.py makemigrations
                             |
  Create superuser (for db)  | python manage.py createsuperuser
                             |
                             |
--------------------------------------------------------------------------------
== Commonly used packages ==
pillow - Image processor
--------------------------------------------------------------------------------
== settings.py ==
* settings.py is the main configuration file for the entire Django project
* THEORY: the way files and functions are referenced here are by "dot notation"
  , in other words, take "INSTALLED_APPS" 'projects.apps.ProjectsConfig' would
  reference the 'projects.apps' file and within that file, it would be referencing
  the "ProjectsConfig" class
    * Lowercase (snake case)text seperated by dots would in fact be similar to
      referencing files within a file structure
    * Camel case (begining with an uppercase characte) would be referencing a class
      withing the preceding "file" referenced in the reference string
--------------------------------------------------------------------------------
== urls.py ==
* urls.py is the url navigation file for the entire Django projects (this the router file)
  Every app can have it's own| if an app has it's own url module, it's important
  url.py                     | to remember to import the view folder:
                             |   from django.urls import Path
                             |   from . import views
                             |
                             | if localized urls.py is reference with an include
                             | statement in the primary urls.py file (parent project
                             | dir, it isn't necessary to reference the project dir
                             |
                             |
  <projectdir>/urls.py       | add include to the import path from django.urls statement
                             |    -->  from django.urls import path, include
                             |
    Referencing urls.py files| when defining paths in the primary urls.py file
    located in app dirs      | if the app has a localized url.py file, when defining
                             | the url path, add a reference to that urls.py file
                             |   i.e: path('playground/', include('playgrounds.urls'))
                             |
  passing in dynamic data    | withing a url definition:
                             | path('projects/', projects, name='projects')
                             | dynamic values can be defined with
                             | <> -> <DATA_TYPE:PARAMETER> -> <str:pk> =
                             |        <string parameter:primary key>
                             |
                             | NOTE: the parameter (in this case, pk) must be references
                             |       within the calling function, i.e.
                             |
                             |      path('projects/<str:pk>/', projects, name='projects')
                             |      ->  def projects(request, pk):
                             |
                             |      path('projects/<str:cookie>/', projects, name='projects')
                             |      ->  def projects(request, cookie):
                             |
* referencing a local urls   | NOTE: the local urls.py must import:
  file (urls.py file within  |       * the path module from django.url
  an app)                    |       * the views file from the currend directory
                             |         --> from django.urls import path
                             |         --> from . import views -> methods are defined here
                             |
                             |       The Primary urls.py file most import
                             |       * the include module from django.urls
                             |
                             |       Within a path definition, the include function
                             |       can be used to reference the local urls.py file
                             |       located inside its respective app, i.e.
                             |       path('', include('projects.urls')) ->
                             |         when the request can not find any other matches
                             |         from the root file pate, it will then look within
                             |         and paths which are reference with include statemets
--------------------------------------------------------------------------------
=== urls summary ===
* when a route is requested (via browser, maybe api) -> the request goes to the urls.py file
* the reference to the request is searched withing the urlpatterns array, which r
  references a function (and any defined dynamic data passed into it from the requester
--------------------------------------------------------------------------------
                             |
                             |
                             |
                             |
                             |
--------------------------------------------------------------------------------
== Django Apps ==
* Django apps are a way of "modularizing" functionality within your django app
--------------------------------------------------------------------------------
== Models ==
* Within any app folder, you will find a models.py file. This file is used to
  define any models associated with its respective app (define any database schema)
--------------------------------------------------------------------------------
== views.py ==
* withing the views.py file, all business logic associated with its respective app
  is defined and managed here.
  start a new view           | def say_hello(request):
                             |   // relies on 'from django.http import HttpResponse'
                             |      return HttpResponse('Hello world')
                             |   when a route hits a view HttpResponse with send output
                             |   * Don't forget to map to a url (urls.py)
                             |
--------------------------------------------------------------------------------
=== templates ===
* The template is generally structured / can be structured as such:
  * There is a primary templates dir which holds templates that apply to the entire Django project
  * there is a templates/<app name> templates dir which holds content that corresponds to the app in question

  The primary tempates dir will contain:
    * the main.html file - the base template which is extended by local template files from respective apps
  The main template is extended by:
    * includes - used to reference other templates within the primary templates dir
       i.e.  {% include 'navbar.html' %}
    * {% block <name> %} references which "pull in" content from within respective app/templates/  files

  The local templates files (located within their own respective app/templates/app dir), each must contain
    * an {% extents 'main.html' %} call to the primary tempates file
    * a {% block <name> %} ... {% endblock <name> %} set of tags which wrap around the content that will be
      "pushed" into the main templates file
                             |
  Interpolate data passed in | `{{ <passed in variable> }}`
  to a template from a view  |
                             | `{% <tags can include logic> %}`
                             |
                             |
                             |

                             |
                             |
  any app dir may have a     | return render(request, <html template>, 'context', MAPPING)
  template dir for templates | return render(request, 'hello.html', )
                             |   relies on from djanglo.shortcuts import render
                             |
                             | NOTE - the render method references the root directory of
                             |        django project, therefore, if a template structure
                             |        is used, then the template must be prefixed with the
                             |        name of it's particular app dir name
                             |        i.e. return render(request, 'projects/hello.html', )
                             |
                             |
                             |
                             |
  interpolated data          | to reference data passed to a template from a view
    data you want to appear  | use double curly braces
    within template          | `{{ <passed in data reference name> }}`
                             |
  interpolate logic          | use {%  %}
    interpolating logic      |    useful for conditionals --> similar to Rails erb files
    within template          |
                             |
  URL Helpers                | the URL helper is simple the name whih is defined
                             | in the utls.py url definition - Name
                             |   i.e.  {% url '<name>' <any variable data> %}
                             |         {% url 'project' project.id %}
--------------------------------------------------------------------------------
== Queries ==
  you must import a model    | fomr .models import ModelName
  before making queries      |
                             |
  standard query             | respons_variable = ModelName.ModelObjectsAttribute.Method()
                             | i.e.    queryset = Project.objects.all()
  other methods              | get one object based on attr      .get()
                             | filter based on criteria          .filter()
                             | exclude based on criteria         .exclude()
                             |
  all() - Retrives all objs  | queryset = ModelName.objects.all()
                             |
  get() - Retrives a single  | queryItem = ModelName.objects.get(attribute='value')
    obj base on matched attr |
                             |
  Filter() - Returns all     | queryset = ModelName.object.filter(attribute='value')
    itmes from table that ma |                            .filter(attribute__startswith='value')
                             |                            .filter(attribute__contains='value')
                             |                            .filter(attribute__icontains='value')
                             |                            .filter(attribute__gt='value')
                             |                            .filter(attribute__gte='value')
                             |                            .filter(attribute__lt='value')
                             |                            .filter(attribute__lte='value')
                             |
  exclute() - Excludes any   | queryset = ModelName.object.exclude(attribute='value')
                             |
  order_by - Order a queryset| queryset = ModelName.object.filter(attribute='value').order_by('value1', 'value2')
                             |
                             |
  reverse order by           | queryset = ModelName.object.filter(attribute='value').order_by('-value', '-value2')
                             |
  create() - Create an inst- | item = ModelName.objects.create(attribute='value')
    ance of a model          |
                             |
  save() - Save changes made | item = ModelName.objects.get(attribute='value')
    to a particular object   | item.title = "New Value"
                             | item.save()
                             |
  delete() - Deletes a       | item = ModelName.objects.last()
    particular item          | item.delete
                             |
  Query Models Children      | item = ModelName.object.first()
                             | item.childmodel_set.all()
                             |
  Query ManyToMany Fields    | item = ModelName.object.first()
                             | item.relationshipname.all()
                             |
  Add ManyToMany Field       | item = ModelName.object.first()
                             | otheritem = OtherModule.ojects.create(attribute='value')
                             | item.relationshipname.add(otheritem)
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |

                             |
                             |
