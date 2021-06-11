# Introduction to Rails discussion questions

Take 30 minutes to discuss the following questions with your table group.

## Rails router

1. What are the seven conventional REST routes for a pizza resource? For each route list the HTTP verb, path and rails controller/action pair.

HTTP    | URI                | Route / Controller Action  | CRUD    |  AR Method                                  | Used for:                                    | SQL                                                                 |
------- | ------------------ | -------------------------- | ------- |  ------------------------------------------ | -------------------------------------------- | ------------------------------------------------------------------- |
GET     | /pizzas          | #index                       | READ    |  Pizza.all                                  | Display a list of all pizzas                 | SELECT * FROM pizzas                                                |
GET     | /pizzas/new      | #new                         | READ    | Pizza.new                                   | Return an HTML form for creating a new pizza |                                                                     |
POST    | /pizzas          | #create                      | CREATE  |  Pizza.create OR .new + .save conditional   | Create a new pizza                           | INSERT INTO pizzas (column1, column2) VALUES (value1, value2)       |
GET     | /pizzas/:id      | #show                        | READ    |  Pizza.find(params[:id])                    | Display a specific pizza                     | SELECT * FROM pizzas WHERE id = :id LIMIT 1                         |
GET     | /pizzas/:id/edit | #edit                        | READ    |  Pizza.find(params[:id])                    | Return an HTML form for editing a pizza      | SELECT * FROM pizzas WHERE id = :id LIMIT 1                         |
PATCH   | /pizzas/:id      | #update                      | UPDATE  |  Pizza.update                               | Update a specific pizza                      | UPDATE pizzas SET column1 = value1, column2 = value2 WHERE id = :id | 
DELETE  | /pizzas/:id      | #destroy                     | DELETE  |  Pizza.find(params[:id]).destroy            | Delete a specific pizza                      | DELETE FROM pizzas WHERE id = :id                                   |


2. What benefits does naming a route provide? (e.g. get '/pizzas, to: 'pizzas#index, as: 'pizzas')

When your Rails application receives an incoming request for:

    - avoid the need to hardcode strings in views
    - reduces the brittleness of a view and makes code easier to understand
    - the id will not need to be specified in the route helper


3. Assuming you are using the standard REST routes, what rails built-in methods can be used to write concise routes?

You can change `get 'pizzas/:id', to: 'pizzas#show'` to:

    resources :pizza ,only: [:index, :show]

- Some performance and memory benefits :)

## Rails Request and Response cycle

1. What are the steps that Rails will take to implement the use cases below? List the verb/path, controller/action and associated SQL.

    - Display a list of resources
        - /pizzas
        select * 
    
    - Delete a resource
        - Text
    
    - Create a new resource
        - Text
    
    - Display one resource
        - retrieve by ID

