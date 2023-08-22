# MindMap-API-Contract

## Node
* Node Object
```
{
  id: integer
  parId: integer
  desc: string
  path: string
}
```
**GET /CreateMindMap**
----
  Create the project with root node, having the parId set to -1, and set it's desc field to the value of desc provided in the request param.
* **URL Params**  
  None
* **Data Params**  
  String desc
* **Headers**  
  Content-Type: application/json  
* **Success Response:**  
* **Code:** 200  
  **Content:**  
```
{
    "id": 1,
    "parId": -1,
    "desc" : "Root Node"
    "path" : "1"
}
```

**POST /CreateNode/:parId**
----
  Creates a new node having and set it's parId to parId and desc to the desc provided in the request param.
* **URL Params**  
  *Required:* `parId=[integer]`
* **Headers**  
  Content-Type: application/json  
* **Data Params**  
  String desc
* **Success Response:**  
* **Code:** 200  
  **Content:**  
```
{
    "id": 2,
    "parId": 1,
    "desc" : "Some text"
    "path" : "1>2"
}
```

**GET /getSubTree/:id**
----
  Returns the subtree starting from given id.
* **URL Params**  
  *Required:* `id=[integer]`
* **Data Params**  
  None
* **Headers**  
  Content-Type: application/json  
* **Success Response:** 
* **Code:** 200  
  **Content:**
```
[
    {
        "id": 1,
        "parId": -1
        "desc": "Root Node",
        "path": "1"
    },
    {
        "id": 2,
        "parId": 1,
        "desc": "Some Node",
        "path": "1>2"
    }
]
```

**DELETE /deleteNode/:id**
----
  Deletes the node and all nodes in the substree of given node.
* **URL Params**  
  *Required:* `id=[integer]`
* **Data Params**  
  None
* **Headers**  
  Content-Type: application/json  
* **Success Response:** 
  * **Code:** 204
  * **Content:** `{ message : "Node deleted successfully" }`
* **Error Response:**  
  * **Code:** 404  
  * **Content:** `{ error : "Node not found" }`


**PATCH /updateNodeDesc/:id**
----
  Updates the desc of the node.
* **URL Params**  
  *Required:* `id=[integer]`
* **Data Params**  
  String desc;
* **Headers**  
  Content-Type: application/json  
* **Success Response:** 
* **Code:** 200  
  **Content:**  `{ message : "Node updated successfully"}`  
* **Error Response:**  
  * **Code:** 404  
  **Content:** `{ error : "Node not found" }`

**PATCH /updateNodeParId/:id**
----
  Updates the desc of the node.
* **URL Params**  
  *Required:* `id=[integer]`
* **Data Params**  
  int parId;
* **Headers**  
  Content-Type: application/json  
* **Success Response:** 
* **Code:** 200  
  **Content:**  `{ message : "Node updated successfully"}`  
* **Error Response:**  
  * **Code:** 404  
  **Content:** `{ error : "Node not found" }`  
