## Gel, a lightweight framework, based on Go serverless functions and lightning fast javascript frameworks

![gellogo](./gellogo.png)

Gel's folder structure is based on Vercel serverless functions projects one. It consists in:
- api folder: contains the Go files and serve each of them as a serverless function
- frontend folder: contains a vite project scafolded with the framework of your choice. Are available at the moment React and Svelte
- public folder: contains the output build of your frontend project

Download the pre release here:
https://github.com/TheWisePigeon/releases/releases/tag/cli

### What to do after creating a new Gel project.
First you want to run 
```bash
vercel
``` 
in the root of the project. This will set up the project and make a deployment to your vercel account(having that you are authenticated)

Once the deployment successful, you can start using your serverless functions and making calls to them from the frontend. External requests might not work because of CORS, but will be fixed in a soon to come update.

Each .go file stands as an endpoint. It contains a function that handles a http request
```go
package api

import (
	// "encoding/json"
	"fmt"
	"net/http"
	// "encoding/json"
)

type JsonResponse struct {
    Message string
    HttpCode int
    Failed bool
}


func Handler(w http.ResponseWriter, req *http.Request){
	fmt.Fprintf(w, "<h1>Hi from Go :)</h1>")
	// u, err := json.Marshal(JsonResponse{Message: "Hello gopher :)", HttpCode: 200, Failed: false})
    //     if err != nil {
    //         panic(err)
    //     }
	// w.Header().Set("Content-Type", "application/json")
	// json.NewEncoder(w).Encode(u) 
}

```
Make sure that all your functions start with a capital letter so that they get exported.

Don't mind opening an issue at the first bug you face :).

Here is an example of a basic url shortener app I wrote. You may check it out for reference.

<script src="https://gist.github.com/hSATAC/5343225.js">
</script>
