---
title       : Chapter about something cool
description : This is what a chapter file looks like on DataCamp.<br>Add some awesome description here.
attachments :
  slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_examle.pdf

--- type:VideoExercise lang:r xp:50 skills:1
## Analyze movie ratings


*** =video_link
//player.vimeo.com/video/108225030

--- type:MultipleChoiceExercise lang:r xp:50 skills:1
## Bad movie

Have a look at the plot that showed up in the viewer to the right. 

Which type of movie has the worst rating assigned to it?

*** =instructions
- Action
- Adventure
- Animation
- Comedy

*** =hint
Have a look at the plot, which color does the point with the lowest y-value have?

*** =pre_exercise_code
```{r}
# The pre exercise code is the perfect moment to preload a dataset. The code below will read the csv
# that is stored at the URL's location and the movies variable will be available in the user's console.

movies <- read.csv("http://s3.amazonaws.com/assets.datacamp.com/course/introduction_to_r/movies.csv")

# Next to reading preloading datasets, we can also preload packages in the pre exercise code. The code
# below will load the ggplot2 library. This makes it available for the user in his/her console.

library(ggplot2)

# In multiple choice exercises, you can ask the user a question about a plot. To make the plot show up
# in the viewer when the user start's the exercise, you can use the plot command in the pre exercise code.

ggplot(movies, aes(x = runtime, y = rating, col = genre)) + geom_point()

```

*** =sct
```{r}
msg_bad <- "That is not correct!"
msg_success <- "Exactly! There seems to be a very bad action movie in the dataset."

# We test the multiple choice exercise, and pass option 1 (- Action in the instructions) as the correct 
# choice. We also pass the test_mc() function a vector of characters to show the correct messages when 
# an answer is tried.
	
test_mc(correct = 1, feedback_msgs = c(msg_success, msg_bad, msg_bad, msg_bad, msg_bad)) 
```

--- type:NormalExercise lang:r xp:100 skills:1
## More movies

In the previous exercise you saw a dataset with some movies, in this exercise we'll have a look at some other dataset about movies!

*** =instructions
- Check the structure of `movie_selection`.
- Select movies with a rating of 5 or higher. Assign the result to `good_movies`.
- Plot `good_movies$Run` on the x axis, `good_movies$Rating` on the y-axis and set `col` to `good_movies$Genre`.

*** =hint
- Use `str()` for the first instruction.
- For the second instruction, you should use `...[movie_selection$Rating >= 5, ]`.
- For the plot, use `plot(x = ..., y = ..., col = ...)`. 

*** =pre_exercise_code
```{r}
# If you load a library in the pre exercise code of a normal exercise, it will be available in the sample code, solution code and
# in the user's console.

library(MindOnStats)

# It's perfectly possible to transform a loaded R dataset in the pre exercise code. You can use this selection in the rest of the
# exercise.

data(Movies)

movie_selection <- Movies[Movies$Genre %in% c("action", "animated", "comedy"),c("Genre", "Rating", "Run")]

# If you don't want variables you used in the pre exercise code to be available in the rest of the exercise, you can clean the up
# at the end of the pre exercise code.

rm(Movies)

```

*** =sample_code
```{r}
# A selection of movies, movie_selection, is available in your workspace

# Check out the structure of movie_selection


# Select movies that have a rating of 5 or higher: good_movies


# Plot the movie run time (Run) on the x axis, Rating on the y axis and set the color using Genre

```

*** =solution
```{r}
# A selection of movies, movie_selection, is available in your workspace

# Check out the structure of movie_selection
str(movie_selection)

# Select movies that have a rating of 5 or higher: good_movies
good_movies <- movie_selection[movie_selection$Rating >= 5, ]

# Plot the movie run time (Run) on the x axis, Rating on the y axis and set the color using Genre
plot(good_movies$Run, good_movies$Rating, col = good_movies$Genre)
```

*** =sct
```{r}
# This is the submission correctness test. Documentation is available at http://docs.datacamp.com/teach/sct-design-r.html

# Test whether the function str is called with the correct argument, object
# If it is not called, print something informative
# If it is called, but called incorrectly, print something else
test_function("str", args = "object",
						  not_called_msg = "You didn't call `str()`!",
						  incorrect_msg = "You didn't call `str(object = ...)` with the correct argument, `object`.")

# Test the object, good_movies
# Notice that we didn't define any feedback here, this will cause automatically generated
# feedback to be prompted to the student in case of an incorrect submission.
test_object("good_movies")

# Test whether the student correctly used plot()
# Again, we use the automatically generated feedback here
test_function("plot", args = "x")
test_function("plot", args = "y")
test_function("plot", args = "col")

# Alternativeley, you can use test_function() like this
# test_function("plot", args = c("x", "y", "col"))
# but this will generate other, less precise, feedback

# It's always smart to include the following line of code at the end of your SCT's
# It will check whether executing the student's code resulted in an error, and 
# will cause the exercise to fail if it did.
test_error()

success_msg("Good work!")
```
