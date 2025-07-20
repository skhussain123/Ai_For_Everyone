

In this lecture series on Python and FastAPI, we are approaching the final stages. As we prepare to dive into a project using FastAPI, it’s essential to understand certain key elements that will help in organizing and structuring the project. Today, we will focus on the HTTP methods used in FastAPI, as understanding these is fundamental before moving on to the project.

1. HTTP Methods – Understanding GET, POST, PUT, DELETE.
2. API Routers – Their use and benefits in organizing a FastAPI application.

## 1. HTTP Methods in FastAPIv
HTTP methods define the actions that can be performed on resources in a RESTful web service. Here, we will discuss four key HTTP methods that are most commonly used in web development: GET, POST, PUT, and DELETE.

### 1.1 GET Method (Retrieve Data)
The GET method is used to retrieve data from the server. In our analogy, this is like asking the waiter at a restaurant to bring you the menu.

* API Analogy: The waiter is your API, and the action of bringing the menu corresponds to retrieving data.
* FastAPI Example: You can use GET to retrieve a list of items from a store or any other resource.

#### Example Code for GET Method:
```bash
from fastapi import FastAPI

app = FastAPI()

@app.get("/")

def read_root():

    """

    This endpoint handles GET requests to the root path ('/').

    It returns a simple welcome message.

    """

    return {"message": "Hello World - This is a GET request example!"}

```

### 1.2 POST Method (Create Resource)
The POST method is used to send data to the server to create a new resource. For example, after choosing an item from the menu, you place an order by telling the waiter what you want to eat.

* API Analogy: You send the order (data) to the waiter (API).
* FastAPI Example: POST is used when you want to create a new resource like adding a new item to the database.

#### Example Code for POST Method:
```bash
@app.post("/items/")

def create_item(item: Item):

    """

    This endpoint handles POST requests to create a new item.

    It expects item data in the request body matching the Item model.

    It returns the created item data with a new item ID.

    """

    item_id = len(items_db) + 1  # Simple ID generation

    items_db[item_id] = item.dict()  # Use dict() to serialize the Pydantic model to a dictionary

    return {"item_id": item_id, **item.dict()} 
```

### 1.3 PUT Method (Update Resource)
The PUT method is used to update an existing resource. For example, after placing your order, you realize you want to change it (like switching from pizza to a sandwich). This is similar to updating an existing resource.

* API Analogy: You call the waiter and update your order.
* FastAPI Example: PUT is used to modify an existing resource on the server, like updating an item's details.

#### Example Code for PUT Method:
```bash
@app.put("/items/{item_id}")

def update_item(item_id: int, item: Item):

    """

    This endpoint handles PUT requests to update an existing item.

    It uses a path parameter `item_id` to identify the item.

    It expects the updated item data in the request body.

    If the item exists, it updates it completely; otherwise, returns a 404 error.

    """

    if item_id not in items_db:


        raise HTTPException(status_code=404, detail="Item not found")


    items_db[item_id] = item.dict()

    return {"item_id": item_id, **item.dict()}

```

### 1.4 DELETE Method (Delete Resource)

The DELETE method is used to delete a resource from the server. For example, if you decide you don’t want the pizza and want to cancel your order, you ask the waiter to delete it.

* API Analogy: You tell the waiter to cancel your order.
* FastAPI Example: DELETE is used to remove a resource from the server, such as deleting an item from the database.

#### Example Code for DELETE Method:
```bash
@app.delete("/items/{item_id}")

def delete_item(item_id: int):

    """

    This endpoint handles DELETE requests to remove an existing item.

    It uses a path parameter `item_id` to identify the item.

    If the item exists, it deletes it and returns a confirmation message.

    Otherwise, it returns a 404 error.

    """

    if item_id not in items_db:

        raise HTTPException(status_code=404, detail="Item not found")

    
    del items_db[item_id]

        return {"message": f"Item {item_id} deleted successfully"}
 

@app.get("/items/")

def get_items():

    """

    This endpoint handles GET requests to retrieve all remaining items.

    It returns a dictionary of items present in the database.

    """

    return items_db
```

## 2. Practical Examples of HTTP Methods in FastAPI
Let’s take a closer look at how these HTTP methods are used in FastAPI with actual examples.

### 2.1 Example of GET Request
The GET method allows us to retrieve data, such as a list of items from a store. Here, we use GET to fetch the list of items.

#### Code Execution for GET:

```bash
@app.get("/items")

def read_items():

    return {"items": ["item1", "item2", "item3"]}
```  

#### Response:
```bash
{

  "items": ["item1", "item2", "item3"]

}
```

#### 2.2 Example of POST Request
The POST method sends data to the server to create a new item. Here, we are creating an item by sending data through the POST request.

#### 2.3 Example of PUT Request
The PUT method updates an existing item. In this case, we are updating an item by changing its name.

#### 2.4 Example of DELETE Request
The DELETE method removes an item. Here, we are deleting an item from the list.

#### 3. Using API Routers in FastAPI
In FastAPI, we can use API routers to group related endpoints and organize our application better.

### 3.1 What Are API Routers?
API routers help us modularize our code, making it cleaner and easier to maintain by grouping related routes.

### 3.2 Example of API Routers
```bash
items_router = APIRouter()

 

items_data: Dict[int, Dict] = {

    101: {"name": "Laptop", "price": 1200},

    102: {"name": "Headphones", "price": 150},

    103: {"name": "Mouse", "price": 30},

}

 

class Item(BaseModel):

    name: str

    price: float

 

class ItemWithId(Item):

    item_id: int

 

@items_router.get("/", response_model=Dict[str, Union[str, List[ItemWithId]]])

def get_all_items():

    items_list_with_ids = [{"item_id": item_id, **item_data} for item_id, item_data in items_data.items()]

    return {"message": "Here are all the items in our shop:", "items": items_list_with_ids}

 

@items_router.get("/{item_id}", response_model=ItemWithId)

def get_item(item_id: int):

    if item_id in items_data:

        return {"item_id": item_id, **items_data[item_id]}

    raise HTTPException(status_code=404, detail="Item not found in this department!")

 

@items_router.post("/", response_model=Dict[str, Union[str, int, Item]])

def create_new_item(item: Item):

    new_id = max(items_data.keys()) + 1 if items_data else 201

    items_data[new_id] = item.dict()

    return {"message": f"Item '{item.name}' added successfully!", "item_id": new_id, **item.dict()}
```    
