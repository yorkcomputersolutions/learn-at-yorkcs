---
title: Build a Space Shooter with MonoGame – 3
author: Jared
type: post
date: 2019-05-20T23:02:38+00:00
url: /2019/05/20/build-a-space-shooter-with-monogame-3/
featured_image: /wp-content/uploads/2019/05/build-space-shooter-monogame-1.jpg
rank_math_internal_links_processed:
  - 1
rank_math_primary_category:
  - 1
rank_math_seo_score:
  - 64
rank_math_robots:
  - 'a:1:{i:0;s:5:"index";}'
rank_math_rich_snippet:
  - article
rank_math_snippet_article_type:
  - BlogPosting
rank_math_snippet_book_editions:
  - 'a:1:{i:0;a:1:{s:11:"book_format";s:9:"Hardcover";}}'
rank_math_snippet_event_type:
  - Event
rank_math_snippet_jobposting_unpublish:
  - on
rank_math_snippet_music_type:
  - MusicGroup
rank_math_snippet_product_instock:
  - on
rank_math_snippet_recipe_instruction_type:
  - SingleField
rank_math_snippet_review_worst_rating:
  - 1
rank_math_snippet_review_best_rating:
  - 5
rank_math_snippet_review_location:
  - bottom
rank_math_snippet_review_shortcode:
  - '[rank_math_review_snippet]'
rank_math_facebook_enable_image_overlay:
  - off
rank_math_facebook_image_overlay:
  - play
rank_math_twitter_use_facebook:
  - on
rank_math_twitter_card_type:
  - summary_large_image
rank_math_twitter_enable_image_overlay:
  - off
rank_math_twitter_image_overlay:
  - play
rank_math_focus_keyword:
  - monogame
rank_math_schema_Article:
  - 'a:6:{s:5:"@type";s:11:"BlogPosting";s:8:"headline";s:11:"%seo_title%";s:13:"datePublished";s:20:"%date(Y-m-dTH:i:sP)%";s:12:"dateModified";s:24:"%modified(Y-m-dTH:i:sP)%";s:6:"author";a:2:{s:5:"@type";s:6:"Person";s:4:"name";s:5:"Jared";}s:8:"metadata";a:3:{s:5:"title";s:7:"Article";s:9:"isPrimary";b:1;s:4:"type";s:8:"template";}}'
rank_math_analytic_object_id:
  - 48
categories:
  - MonoGame
series:
  - Build a Space Shooter with MonoGame
tags:
  - 'C#'
  - 'C# game'
  - csharp
  - MonoGame

---
Now, we know every game worth it’s money has a game state system of some sort. &nbsp;I mean this as in, most games have a main menu, a play state, and a game over state. &nbsp;Something like that. We will have to build this sort of system. For this, we will be utilizing the _enum_ type in C#. &nbsp;Just after where we initialize the field _arialHeading_, add the following to define an enum named _GameState_:

{{<highlight cs>}}
enum GameState
{
	MainMenu,
	Gameplay,
	GameOver
}
{{</highlight>}}

We will also want to initialize a property to keep track of the current game state:

{{<highlight cs>}}
private GameState _gameState;
{{</highlight>}}

The next step to setup our game state system is to add some logic to the _Update_ method of _Game1.cs_. &nbsp;After the comment, “TODO: Add your update logic here,” add the following:

{{<highlight cs>}}
switch (_gameState) {
	case GameState.MainMenu:
    	{
        	UpdateMainMenu(gameTime);
        	break;
    	}

	case GameState.Gameplay:
    	{
        	UpdateGameplay(gameTime);
        	break;
    	}

	case GameState.GameOver:
    	{
        	UpdateGameOver(gameTime);
        	break;
    	}
}
{{</highlight>}}

The switch statement allows us to check which game state is currently set a little more compactly than an if statement. &nbsp;Let’s define the methods that we specified for each case in our switch statement. Add the following methods after the _Update_ method but before the _Draw_ method:

{{<highlight cs>}}
private void UpdateMainMenu(GameTime gameTime) {


}

private void UpdateGameplay(GameTime gameTime) {

}

private void UpdateGameOver(GameTime gameTime) {


}
{{</highlight>}}

We will also want to add two additional methods for resetting gameplay and changing the game scene:

{{<highlight cs>}}
private void resetGameplay()
{

}

private void changeGameState(GameState gameState)
{
	
}
{{</highlight>}}

In the Draw method of _Game1.cs_, add the following code after the comment, “TODO: Add your drawing code here”:

{{<highlight cs>}}
spriteBatch.Begin(SpriteSortMode.Deferred, BlendState.AlphaBlend, SamplerState.PointWrap);

switch (_gameState)
{
	case GameState.MainMenu:
    	{
        	DrawMainMenu(spriteBatch);
        	break;
    	}

	case GameState.Gameplay:
    	{
        	DrawGameplay(spriteBatch);
        	break;
    	}

	case GameState.GameOver:
    	{
        	DrawGameOver(spriteBatch);
        	break;
    	}
}

spriteBatch.End();
{{</highlight>}}

It’s important to point out that in order to draw anything in MonoGame, you need to have all of your draw calls between the calls: _spriteBatch.Begin_ and _spriteBatch.End_. &nbsp;It’s also worth mentioning that the last parameter of our _spriteBatch.Begin_ call tells the game we don’t want to smooth images, in order to preserve our crisp pixel art. &nbsp;While we’re at it, change the following line at the top of the _Draw_ method:

{{<highlight cs>}}
GraphicsDevice.Clear(Color.CornflowerBlue);
{{</highlight>}}

To  

{{<highlight cs>}}
GraphicsDevice.Clear(Color.Black);
{{</highlight>}}

As we did with the update methods for our game states, we will add draw methods for each of our game states. &nbsp;Add the following methods after the _Draw_ method:

{{<highlight cs>}}
private void DrawMainMenu(SpriteBatch spriteBatch) {


}

private void DrawGameplay(SpriteBatch spriteBatch) {


}

private void DrawGameOver(SpriteBatch spriteBatch) {


}
{{</highlight>}}


Finally, we will need to add a few methods we will be using in our game class as well as others:

{{<highlight cs>}}
public static int randInt(int minNumber, int maxNumber)
{
	return new Random().Next(minNumber, maxNumber);
}

public static float randFloat(float minNumber, float maxNumber)
{
	return (float)new Random().NextDouble() * (maxNumber - minNumber) + minNumber;
}
{{</highlight>}}


The next thing we will do is define our other classes. &nbsp;We will start by creating a new class named _AnimatedSprite.cs_. &nbsp;We can add a new class by going to the Solution Explorer, right click our project directory, move the mouse over the add option, then click “New Item…”  

![](https://learn.yorkcs.com/wp-content/uploads/2019/05/solution_explorer_add_class-2.png)

A new prompt will appear allowing us to choose the file template we want, as well as name the file. &nbsp;By default, Visual Studio should have the class template selected, so we can just enter the name we want. &nbsp;Like I said before, we will be naming this class, _AnimatedSprite.cs_. &nbsp;Once you’re done with that, click the add button, and our new class should be added to our project. &nbsp;Let’s get started diving deep into these classes!  


We will start by opening _AnimatedSprite.cs_. &nbsp;The following two using statements will be required in this class, so add them to the other using statements at the top of the file:

{{<highlight cs>}}
using Microsoft.Xna.Framework;
using Microsoft.Xna.Framework.Graphics;
{{</highlight>}}

Next, we will need to add some fields and properties that all animated sprites will have in common. &nbsp;What are they? We will need to store the width and height of each frame, the duration of each frame, the amount of frames, the current frame, and the different fields for the timer. &nbsp;We will also have to keep track if an animation can repeat, and if that animation can’t repeat, we need to know if the animation has finished playing.

{{<highlight cs>}}
private Texture2D texture;
public int frameWidth { get; set; }
public int frameHeight { get; set; }
public int duration { get; set; }
public Rectangle sourceRect { get; set; }
public int amountFrames { get; set; }
public int currentFrame { get; set; }
private int updateTick = 0;
private bool _repeats = true;
public void setCanRepeat(bool canRepeat)
{
	_repeats = canRepeat;
}
private bool _finished = false;
public bool isFinished()
{
	return _finished;
}
{{</highlight>}}

The next step is to add the constructor. &nbsp;We will be taking in a texture, the frame width, the frame height, and the duration of the animation. &nbsp;We can figure out the rest inside the class once it’s instantiated. Add the following code to create our constructor:

{{<highlight cs>}}
public AnimatedSprite(Texture2D texture, int frameWidth, int frameHeight, int duration)
{
	this.texture = texture;
	this.frameWidth = frameWidth;
	this.frameHeight = frameHeight;
	this.duration = duration;
	amountFrames = this.texture.Width / this.frameWidth;
	sourceRect = new Rectangle(currentFrame * this.frameWidth, 0, this.frameWidth, this.frameHeight);
}
{{</highlight>}}

Finally we will need to add an _Update_ method to our _AnimatedSprite_ class. &nbsp;The instructions we’re trying to execute each frame looks kind of like the following:  


IF updateTick < duration THEN

&nbsp;&nbsp;&nbsp; Add _1_ to updateTick

ELSE

&nbsp;&nbsp;&nbsp; IF currentFrame < amountFrames &#8211; 1 THEN

&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; Add _1_ to currentFrame

&nbsp;&nbsp;&nbsp; ELSE

&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; IF _repeats THEN

&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; Set currentFrame to __.

&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; ELSE

&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; Set finished to _true_

&nbsp;&nbsp;&nbsp; Set the source rectangle to the update rectangle

&nbsp;&nbsp;&nbsp; Set updateTick to __



Let’s add the following to write our _Update_ method and above with real C#:

{{<highlight cs>}}
public void Update(GameTime gameTime)
{
	if (updateTick < duration)
	{
    	updateTick++;
	}
	else
	{
    	if (currentFrame < amountFrames - 1)
    	{
        	currentFrame++;
    	}
    	else
    	{
        	if (_repeats)
        	{
            	currentFrame = 0;
        	}
        	else
        	{
            	_finished = true;
        	}
    		}

    	sourceRect = new Rectangle(currentFrame * this.frameWidth, 0, this.frameWidth, this.frameHeight);
    	updateTick = 0;
	}
}
{{</highlight>}}

We are now finished writing the _AnimatedSprite_ class! 

Let&#8217;s move on to [part four][1]!

 [1]: https://learn.yorkcs.com/2019/05/20/build-a-space-shooter-with-monogame-4/