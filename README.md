# Forkify

Javascript application that utilizes the Forkify API to fetch and display food recipes.

We used user stories to discover the following desires users have for the product to inform what features should be included in the application. 
		
**Application features based upon user stories:**
 - Search for Recipes  
	 -	Search functionality: input field to send request to API with searched keywords
	 -	Display results with pagination
	 -	Display recipe with cooking time, servings and ingredients
 - Update the number of servings 
	 -	Change servings functionality to be updated to number of servings selected by user
 - Bookmark recipes 
	 -	Display a list of all bookmarked recipes by user
 - Create my own recipes 
	 -	User can upload own recipes
	 -	User recipes will automatically be bookmarked
	 -	User can only see their own recipes, not recipes from other users
 - See my bookmarks and own recipes after having left the app and returned
	 -	Store bookmark data in the browser using local storage
	 -	On page load, read saved bookmarks from local storage and display
													 
## Model View Controller Architecture
  
 **Model**: Business, state, and HTTP library related logic. 
 
  **Controller**: Application logic that handles UI events and dispatches tasks to model and view. 

   **View**: Presentation logic
  
  ***Example:***  MVC Flow for recipe display 
 - When the user selects a recipe or inputs a link to a recipe in the search bar, those events cause the **controller** to call a function in the **model**. 
 - The **model** at that point, asynchronously gets the recipe data from the API. 
 - The data is stored in a state object inside of the **model**. 
 - When the data has arrived, the **controller** receives the data and  sends it to the **view**.
 - The **view** renders the recipe on the screen. 

## Function Details (recipe display)

 1. In the above example, the **controller** calls the **controlRecipes( )** function. There is a try catch block inside of this function that contains a variable '**id**' assigned to the recipe id collected during the UI event. 

 2. The **renderSpinner( )** function is called inside of the **view** to load the spinner markup on the screen while the user waits for the recipe to be loaded. 
 3. We use the **await** keyword in front of the call for the **model.loadRecipe( id )** function, because this is asynchronous logic. 
 4. When the **model** has received the data, the **createRecipeObject( data )** function is called to format and return the recipe related information.
 5. The **controller** awaits the data from **model.loadRecipe( id )**
 6. The **controller** renders the recipe via the **recipeView.render( model.state.recipe )** function call.
 7. The **view** calls the **generateMarkup( )** function on this recipe data where the markup is generated
