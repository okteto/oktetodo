Now we have to make the application work with Okteto without adding any K8s manifests and just using Docker compose. The first part is removing all the localhost references from the frontend code.

Replacing:
```
    await fetch(`http://localhost:5050/todos/${todo.todo_id}`, {
```
with:
```
    await fetch(`/todos/${todo.todo_id}`, {
``` 

The second thing I had to do was add the `endpoints` section to the `docker-compose.yaml` otherwise it won't know how to show me the endpoints on the Okteto UI.

And that was all that was needed! Run `okteto deploy` and `okteto up` and everything should be working as expected.

Third thing was to avoid the creation of separate frontend and backend microservices (which didn't really work) we needed to remove the port forwarding from the `docker-compose`. That is reaplce this:
```
    ports:
      - 5050:5050
```
with:
```
    ports:
      - 5050
```