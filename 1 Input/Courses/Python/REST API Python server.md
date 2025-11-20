We can use `fastAPI` to create our application.
```
from fastapi import FastAPI // framework to built application
from pydantic import BaseModel //library to parse and validate, create data
import uvicorn // light webserver to run Python app

app = FastAPI("simply library app")

books_db = [] // local database
current_id = 1

class Book(BaseModel):
	id: Optional[int] = None
	title: str
	author: str
	pages: int
	
@app.get("/books", response_model=List[Book])
def get_all_books():
	return books_db
	
@app.post("/books", response_Model=Book, status_code=201)
def create_book(book: Book):
	global current_id
	book.id = current_id
	current_id += 1
	
	books_db.append(book)
	return book
	
if __name__ == "__main__":
	uvicorn.run("main:app", host="0.0.0.0", port=8000)
```

Simple REST API application. We can then run `docker_compose up --build`, and while running our webserver on localhost, we can make requests to it using `curl`.

Links:

202511132212

