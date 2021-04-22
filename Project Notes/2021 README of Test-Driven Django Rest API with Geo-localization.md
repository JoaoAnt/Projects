# Why Only the readme?
At the moment this project is private and it has entered a competition, as soon as the competition ends and results come out and if the project is not sold it will become fully available here. In the meanwhile, here is the README that explains some of the thought processes behind it.

# Minimum Requesites:
## Day 17 Apr
    Required:
    - DONE Create API Rest
    - DONE Create Model
    - DONE Create PostgresQL database
    - DONE Create endpoints
    - DONE Create User authentication (can create the endpoints myself)
    - DONE Protect endpoints
    - DONE Include PostGis into PostgresQL database
    - DONE Only Owner or Admin can change the Events
    - DONE Make State only change by admin
    - DONE Filter by owner, category and state

    Extra to the Required:
    - DONE Search Filter in the Users that search in Email and username

## Day 18 Apr
    Required:
    - DONE Comment all the view, Endpoints, Filters and Permissions
    - DONE Filter by Localization
    - DONE Deploy everything into Docker Compose
    - DONE Use the docker image selected
    - DONE Auto Documentation swagger, swagger.json, swagger.yaml, redoc
    - DONE Place everything into Git
    - DONE Create instructions in how to open the project and notes on README
    - DONE Create a collection of Endpoints

## Day 19 Apr
    - DONE Test for model and for endpoints that require authentication 



# Street Occurrences
One weekend backend django with PostGis Project.

## Used Technologies
* [Django](https://www.djangoproject.com/): The web framework for perfectionists with deadlines (Django builds better web apps with less code).
* [DRF](www.django-rest-framework.org/): A powerful and flexible toolkit for building Web APIs
* [Docker](https://www.docker.com/): Empowering App Development for Developers


## Installation
* If you wish to run your own build, first ensure you have python globally installed in your computer. If not, you can get python [here](https://www.python.org").
* Turn on Docker on your local machine.
* Then, Git clone this repo to your PC
    ```bash
        $ git clone https://github.com/JoaoAnt/streetEvents
    ```
* To build the containers
    ```bash
        $ docker-compose build
    ```
* To have the docker up and running:
    ```bash
        $ docker-compose up
    ```
* You can now access the file api service on your browser by using
    ```
        http://localhost:8000/
    ```

## Testing
* Run the command:
    ```bash
        $ docker-compose run --rm web sh -c "python streetEvent/manage.py test events"
    ```
## Authentication & User Creation
* HTTP Authorization Scheme	`basic`

* Admin users should be created using:
    ```bash
        $ docker-compose run web python streetEvent/manage.py createsuperuser
    ```
* Non-Admin users can be created in POST `/users/` or through manage.py


## API Endpoints
* Dynamic documentation
    ```
    /swagger
    /redoc
    ```
* Static Documentation
    ```
    /swagger.json
    /swagger.yaml
    /swagger?format=openapi
    ```

* Authentication
    ```
    /api-auth
    ```

* Events Endpoints
    ```
    /events/ - GET, POST
    /events/{id}/ - GET, PUT, PATCH, DELETE
    ```

* Users Endpoints
    ```
    /users/ - GET, POST
    /users/{id}/ - GET, PUT, PATCH, DELETE
    ```

### Filters
- `/events`:
    - Query on `state`, `owner`, `category` and `page`.
    - Query in url in `lat`, `lng` and `rnd` (the `rnd` is optional, the other two are required to use this query).

This filter can be used simultaneously, here are some examples is request URL:
```
http://127.0.0.1:8000/events/?state=To%20Validate
http://127.0.0.1:8000/events/?lat=50&lng=10&rnd=18
http://127.0.0.1:8000/events/?lat=50&lng=10&rnd=18&state=To%Validate
```
- `/users`:
    - Search Query on `username` and `email address`.

