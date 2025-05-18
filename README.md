1:
[REST API basics- CRUD, test & variable.postman_collection.json](https://github.com/user-attachments/files/20274348/REST.API.basics-.CRUD.test.variable.postman_collection.json)
авто тест
import requests

BASE_URL = "https://jsonplaceholder.typicode.com/posts"

def test_create_post():
    data = {
        "title": "test title",
        "body": "test body",
        "userId": 1
    }
    response = requests.post(BASE_URL, json=data)
    assert response.status_code == 201
    json_data = response.json()
    assert "id" in json_data
    assert json_data["title"] == data["title"]

def test_update_post():
    update_data = {
        "id": 1,
        "title": "updated title",
        "body": "updated body",
        "userId": 1
    }
    response = requests.put(f"{BASE_URL}/1", json=update_data)
    assert response.status_code == 200
    json_data = response.json()
    assert json_data["title"] == "updated title"

def test_delete_post():
    response = requests.delete(f"{BASE_URL}/1")
    assert response.status_code == 200
