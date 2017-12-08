# Campus Manager App Instructions

Campus Manager is a web application that lets you manage different campuses and students in those campuses.



# Start With Database Models
* Make sure your postgres database is setup and is working/listening (**server/db/index.js**)
* Create a campus.js, student.js files inside the db folder.
    ##### Campus Model:
    * name (not empty or null)
    * imageUrl
    * description (large text... use the TEXT data type in sequelize)
    ##### Student Model:
    * firstName (not null)
    * lastName (not null)
    * email (not null and valid email)
    * gpa
    * Must have a virtual field 'name' which gives you the full name
* Once you're done with campus and student, create **index.js** inside the same folder.
* In the index.js file, import all the models and make the relationship between the models. Export the file.

# Build your routes and controllers (see workflow example)
* Create two folders **api** and **controllers** in the same **db** folder
* In the **controllers** folder, create two files **campus.js** **student.js**.
    * All the logic of handling requests for campuses will sit inside of **campus.js** and same applies for handling student requests in **student.js**
    * **campus.js** should have the following functions for requests
        | Functions | Description |
        | ------ | ------ |
        | **getCampuses** | gets all campuses in the database |
        | **createCampus** | creates a new campus |
        | **getSingleCampus** | gets a specific campus |
        | **updateSingleCampus** |  updates a specific campus |
        | **deleteSingleCampus** | deletes a specific campus |
    * **student.js** should have the following functions for requests
        | Functions | Description |
        | ------ | ------ |
        | **getStudents** | gets all students in the database |
        | **createStudent** | creates a new student |
        | **getSingleStudent** | gets a specific student |
        | **updateSingleStudent** |  updates a specific student |
        | **deleteSingleStudent** | deletes a specific student |
* In the **api** folder, create a file **index.js**. This file will map all your routes(path) to your controllers(logic).
    **Note: Make sure to import your controllers**
    > apiRouter.get('/api/campuses', campusesController.getCampuses);
    > apiRouter.post('/api/campuses', campusesController.createCampus);
    > Now make one for getting single campus, updating and deleting a campus.

    > apiRouter.get('/api/students', studentsController.getStudents);
    > apiRouter.post('/api/students', studentsController.createStudent);
    > Now make one for getting single student, updatting and deleting a student.

# A Sample Workflow for Building Routes and Controllers
1. Create **index.js** in **api** folder.
2. Create a *POST* request for creating a campus.
    * **Example:** **Note:** Pretend you've already created a **createCampus** function in your controller.
        ```javascript
        apiRouter.post('/api/campuses', campusesController.createCampus)
        ```

3. Create a **campus.js** file in **controllers** folder.
4. Create a **createCampus** function that handles the logic of the *POST request* for your route.
    * **Example:**
        ```javascript
            exports.createCampus = function(req, res) {
                if (!req.body.name) return;
                return Campus
                    .create(req.body)
                    .then(campus => res.send(campus));
            }
        ```
5. Open up **POSTMAN** app and start testing the routes by submitting post requests and adding RAW JSON content.
6. Once you've tested and made sure the route and the specific controller function works, move on to the next one.
7. REPEAT the same process for all the other **controller** functions and **routes**.

---

# BACKEND DONE 🔥 👍 🙌

---

# Start with React Components (workflow example)
- Think about what components you need, which components should be class based vs pure functions
- Create a **Home.jsx** in the **components** folder.
- Since **navbar** is a global component, it makes sense to put that as the **first** thing in **home.jsx**
- Then start working your way down and think about what you need.
- Ok you want to show the campuses, then you need to make sure to get the routes working.
- So, you import the **Route** from **react-router-dom**
- Add a dummy route like
    ```<Route exact path='/' render={() => <div>hello i'm just a dummy</div>} />```
- Now, dummy data is cool but you need to show all the schools so create **AllSchools.jsx** component.
- Get some div with dummy data working in **AllSchools.jsx**.
- Include that in the **Home.jsx**:
    ```<Route exact path='/' render={() => <AllSchools /> }```
- Alright, now that's cool but you need to show some real data i.e. **schools**
- So...

# Action Creators && Reducers
- Create action types.
- Create Actions
- Create Thunks
- Create Reducers

1. Once you have created the right actions/reducers, let's say something is returning **schoolObjList**, you have to pass those into the component, in this case, i.e. **Allschools.jsx**
2. Go to **home.jsx**, and pass props/thunks into the Route component ```<Route exact path='/' render={() => <AllSchools schoolsObjList={schoolObjList}/> }```
    **Note:** Make sure to import and export all the files necessary!
3. Go back to **AllSchools.jsx**. Now, **schoolObjList** should be available there. And write a function that displays all of them on the page.
    * **Example:**
    ```javascript
    {
        schoolObjList.map(school => {
            return (
                <div style={{ "text-align": "center" }} className = 'col-lg-6' key={school.id}>
                    <Link to={`/schools/${school.id}`}>
                        <img height='400' width='400' src={school.imageUrl}/><br>
                        {school.name}    
                    </Link>
                </div>
            )   
        })        
    }
    ```
4. Now write another function called **onFormSubmit** in **AllSchools.jsx** and that should trigger on a click event.
5. Follow similar process for all other events, components, routes, actions, reducers

---
# ******************************************* GOOD LUCK *****************************************
