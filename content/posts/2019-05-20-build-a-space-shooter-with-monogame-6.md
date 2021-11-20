---
title: Build a Space Shooter with MonoGame – 6
author: Jared
type: post
date: 2019-05-20T23:03:07+00:00
url: /2019/05/20/build-a-space-shooter-with-monogame-6/
featured_image: /wp-content/uploads/2019/05/build-space-shooter-monogame-1.jpg
rank_math_internal_links_processed:
  - 1
rank_math_primary_category:
  - 184
rank_math_seo_score:
  - 22
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
rank_math_schema_Article:
  - 'a:6:{s:5:"@type";s:11:"BlogPosting";s:8:"headline";s:11:"%seo_title%";s:13:"datePublished";s:20:"%date(Y-m-dTH:i:sP)%";s:12:"dateModified";s:24:"%modified(Y-m-dTH:i:sP)%";s:6:"author";a:2:{s:5:"@type";s:6:"Person";s:4:"name";s:5:"Jared";}s:8:"metadata";a:3:{s:5:"title";s:7:"Article";s:9:"isPrimary";b:1;s:4:"type";s:8:"template";}}'
rank_math_analytic_object_id:
  - 46
categories:
  - MonoGame
series:
  - Build a Space Shooter with MonoGame
tags:
  - 'C#'
  - 'C# game'
  - cross-platform
  - crossplatform
  - crossplatform game
  - csharp
  - csharp game
  - MonoGame

---
Now that we’re done with the classes for our game object’s, let’s create one more class for our menu buttons. &nbsp;Add a new class named _MenuButton.cs_. &nbsp;In that class, add the usual two using statements. &nbsp;This class does not need to extend anything. Next, add the following fields and properties:

<pre class="EnlighterJSRAW" data-enlighter-language="csharp" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">private Game1 game;
private Vector2 position;
private Texture2D texDefault;
private Texture2D texOnDown;
private Texture2D texOnHover;
private Texture2D currentTexture;
public Rectangle boundingBox;

public bool isActive { get; set; }
public bool lastIsDown = false;
private bool _isDown = false;
private bool _isHovered = false;</pre>

Then we will add two methods for setting whether the button is pushed down or not, and whether the mouse is hovering over the button or not. &nbsp;In addition we will be adding a third method to update the texture of the button:

<pre class="EnlighterJSRAW" data-enlighter-language="csharp" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">public void SetDown(bool isDown)
{
	if (!_isDown && isDown)
	{
    	game.sndBtnDown.Play();
	}
	_isDown = isDown;

	ChangeTexture();
}
public void SetHovered(bool isHovered)
{
	if (!_isHovered && !_isDown && isHovered)
	{
    	game.sndBtnOver.Play();
	}
	_isHovered = isHovered;

	ChangeTexture();
}

private void ChangeTexture()
{
	if (_isDown)
	{
    	currentTexture = texOnDown;
	}
	else
	{
    	if (_isHovered)
    	{
        	currentTexture = texOnHover;
    	}
    	else
    	{
        	currentTexture = texDefault;
    	}
	}
}</pre>

After that, let’s add our constructor:

<pre class="EnlighterJSRAW" data-enlighter-language="csharp" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">public MenuButton(Game1 game, Vector2 position, Texture2D texDefault, Texture2D texOnDown, Texture2D texOnHover)
{
	this.game = game;
	this.position = position;
	this.texDefault = texDefault;
	this.texOnDown = texOnDown;
	this.texOnHover = texOnHover;
	currentTexture = this.texDefault;
	boundingBox = new Rectangle((int)position.X, (int)position.Y, this.texDefault.Width, this.texDefault.Height);
}</pre>

Finally, we can conclude _MenuButton.cs_ with the _Draw_ method:

<pre class="EnlighterJSRAW" data-enlighter-language="csharp" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">public void Draw(SpriteBatch spriteBatch)
{
	if (isActive)
	{
    		spriteBatch.Draw(currentTexture, position, Color.White);
	}
}</pre>

At this point, we can hop back over to _Game1.cs_. &nbsp;In _Game1.cs_, right under where we set the current game state, add the following:

<pre class="EnlighterJSRAW" data-enlighter-language="csharp" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">private KeyboardState keyState = Keyboard.GetState();</pre>

The above line is used for the movement logic. &nbsp;After this line, we will want to define two menu buttons for the play button and the restart button:

<pre class="EnlighterJSRAW" data-enlighter-language="csharp" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">private MenuButton playButton;
private MenuButton restartButton;</pre>

Then, we will add several lists for keeping track of explosions, enemies, lasers, and the like:

<pre class="EnlighterJSRAW" data-enlighter-language="csharp" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">private List&lt;Explosion> explosions = new List&lt;Explosion>();
private List&lt;Enemy> enemies = new List&lt;Enemy>();
private List&lt;EnemyLaser> enemyLasers = new List&lt;EnemyLaser>();
private List&lt;PlayerLaser> playerLasers = new List&lt;PlayerLaser>();
private Player player = null;
private ScrollingBackground scrollingBackground;</pre>

Next, let’s add two lines for the restart timer, which will be used when the player is destroyed:

<pre class="EnlighterJSRAW" data-enlighter-language="csharp" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">private int restartDelay = 60 * 2;
private int restartTick = 0;</pre>

After that, we need to add two more lines for the enemy spawner timer:

<pre class="EnlighterJSRAW" data-enlighter-language="csharp" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">private int spawnEnemyDelay = 60;
private int spawnEnemyTick = 0;</pre>

Then, let’s write two more lines for the player shoot timer:

<pre class="EnlighterJSRAW" data-enlighter-language="csharp" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">private int playerShootDelay = 15;
private int playerShootTick = 0;</pre>

In the Initialize method of _Game.cs_, we can set the mouse to be visible when you move it over the game window:

<pre class="EnlighterJSRAW" data-enlighter-language="csharp" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">IsMouseVisible = true;</pre>

We can also set the width and height of the game window:

<pre class="EnlighterJSRAW" data-enlighter-language="csharp" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">graphics.PreferredBackBufferWidth = 480;
graphics.PreferredBackBufferHeight = 640;</pre>

Finally, we have to apply the changes in order for these properties to take effect.

<pre class="EnlighterJSRAW" data-enlighter-language="csharp" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">graphics.ApplyChanges();</pre>

Let’s take another look at the _LoadContent_ method. &nbsp;At the bottom after we load our SpriteFont, add the following few lines to instantiate our scrolling background, create our menu buttons, and change the game scene to the main menu:

<pre class="EnlighterJSRAW" data-enlighter-language="csharp" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">scrollingBackground = new ScrollingBackground(texBgs);


playButton = new MenuButton(this, new Vector2(graphics.PreferredBackBufferWidth * 0.5f - (int)(texBtnPlay.Width * 0.5), graphics.PreferredBackBufferHeight * 0.5f), texBtnPlay, texBtnPlayDown, texBtnPlayHover);
restartButton = new MenuButton(this, new Vector2(graphics.PreferredBackBufferWidth * 0.5f - (int)(texBtnPlay.Width * 0.5), graphics.PreferredBackBufferHeight * 0.5f), texBtnRestart, texBtnRestartDown, texBtnRestartHover);


changeGameState(GameState.MainMenu);</pre>

Let’s take another look at the _Update_ method. &nbsp;Right after “TODO: Add your update logic here,” but before the switch statement, add:

<pre class="EnlighterJSRAW" data-enlighter-language="csharp" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">keyState = Keyboard.GetState();

scrollingBackground.Update(gameTime);</pre>

Next, let’s fill in the _UpdateMainMenu_ method. &nbsp;Pretty much, all we’re doing in this method is to update the menu button state depending on the mouse state and position. &nbsp;If the mouse moves over the player button, it will play the hover sound and display the hover texture. If the mouse button is pressed while the mouse is over the play button, the button down sound will play and the corresponding texture will be show. &nbsp;Let’s add the following to _UpdateMainMenu_:

<pre class="EnlighterJSRAW" data-enlighter-language="csharp" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">if (playButton.isActive)
{
	MouseState mouseState = Mouse.GetState();

	if (playButton.boundingBox.Contains(mouseState.Position))
	{
    	if (mouseState.LeftButton == ButtonState.Pressed)
    	{
        	playButton.SetDown(true);
        	playButton.SetHovered(false);
    	}
    	else
    	{
        	playButton.SetDown(false);
        	playButton.SetHovered(true);
    	}

    	if (mouseState.LeftButton == ButtonState.Released && playButton.lastIsDown)
    	{
        	changeGameState(GameState.Gameplay);
    	}
	}
	else
	{
    	playButton.SetDown(false);
    	playButton.SetHovered(false);
	}

	playButton.lastIsDown = mouseState.LeftButton == ButtonState.Pressed ? true : false;
}
else
{
	playButton.isActive = true;
}</pre>

I’ll give a brief rundown what we’ll be doing in the _UpdateGameplay_ method. &nbsp;If the player doesn’t exist yet (when the game starts), we create an instance of it and assign it to the player field. &nbsp;At the same time we will be updating the restart timer. After that we update the player’s movement (via the keyboard checks). &nbsp;Then we restrict the player position to the bounds of the screen. We also want to update all of the game object lists, as well as check for collisions. &nbsp;Let’s start by the initial check testing whether the player is null or not. Add the following to the _UpdateGameplay_ method:

<pre class="EnlighterJSRAW" data-enlighter-language="csharp" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">if (player == null) {
	player = new Player(texPlayer, new Vector2(graphics.PreferredBackBufferWidth * 0.5f, graphics.PreferredBackBufferHeight * 0.5f));
}
else {
	player.body.velocity = new Vector2(0, 0);

if (player.isDead())
{
	if (restartTick &lt; restartDelay)
	{
    	restartTick++;
	}
	else
	{
    	changeGameState(GameState.GameOver);
    	restartTick = 0;
	}
}
else
{
	if (keyState.IsKeyDown(Keys.W))
	{
    	player.MoveUp();
	}
	if (keyState.IsKeyDown(Keys.S))
	{
    	player.MoveDown();
	}
	if (keyState.IsKeyDown(Keys.A))
	{
    	player.MoveLeft();
	}
	if (keyState.IsKeyDown(Keys.D))
	{
    	player.MoveRight();
	}
	if (keyState.IsKeyDown(Keys.Space))
	{
    	if (playerShootTick &lt; playerShootDelay)
    	{
        	playerShootTick++;
    	}
    	else
    	{
        	sndLaser.Play();
        	PlayerLaser laser = new PlayerLaser(texPlayerLaser, new Vector2(player.position.X + player.destOrigin.X, player.position.Y), new Vector2(0, -10));
        	playerLasers.Add(laser);
        	playerShootTick = 0;
    	}
	}
}

player.Update(gameTime);

player.position.X = MathHelper.Clamp(player.position.X, 0, graphics.PreferredBackBufferWidth - player.body.boundingBox.Width);
player.position.Y = MathHelper.Clamp(player.position.Y, 0, graphics.PreferredBackBufferHeight - player.body.boundingBox.Height);
}</pre>

After this check, we will be updating entity positions:

<pre class="EnlighterJSRAW" data-enlighter-language="csharp" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">/**
* UPDATE ENTITY POSITIONS
**/
for (int i = 0; i &lt; playerLasers.Count; i++)
{
	playerLasers[i].Update(gameTime);

	if (playerLasers[i].position.Y &lt; 0)
	{
    	playerLasers.Remove(playerLasers[i]);
    	continue;
	}
}

for (int i = 0; i &lt; enemyLasers.Count; i++)
{
	enemyLasers[i].Update(gameTime);

	if (player != null)
	{
    	if (!player.isDead())
    	{
        	if (player.body.boundingBox.Intersects(enemyLasers[i].body.boundingBox))
        	{
            	sndExplode[randInt(0, sndExplode.Count - 1)].Play();
            	Explosion explosion = new Explosion(texExplosion, new Vector2(player.position.X + player.destOrigin.X, player.position.Y + player.destOrigin.Y));
            	explosions.Add(explosion);

            	player.setDead(true);
        	}
    	}
	}

	if (enemyLasers[i].position.Y > GraphicsDevice.Viewport.Height)
	{
    	enemyLasers.Remove(enemyLasers[i]);
	}
           	 
}

for (int i = 0; i &lt; enemies.Count; i++)
{
	enemies[i].Update(gameTime);

	if (player != null)
	{
    	if (!player.isDead())
    	{
        	if (player.body.boundingBox.Intersects(enemies[i].body.boundingBox))
        	{
            	sndExplode[randInt(0, sndExplode.Count - 1)].Play();
            	Explosion explosion = new Explosion(texExplosion, new Vector2(player.position.X + player.destOrigin.X, player.position.Y + player.destOrigin.Y));
            	explosions.Add(explosion);

            	player.setDead(true);
        	}

        	if (enemies[i].GetType() == typeof(GunShip))
        	{
            	GunShip enemy = (GunShip)enemies[i];

            	if (enemy.canShoot)
            	{
                	EnemyLaser laser = new EnemyLaser(texEnemyLaser, new Vector2(enemy.position.X, enemy.position.Y), new Vector2(0, 5));
                	enemyLasers.Add(laser);

                	enemy.resetCanShoot();
            	}
        	}
        	if (enemies[i].GetType() == typeof(ChaserShip))
        	{
            	ChaserShip enemy = (ChaserShip)enemies[i];

            	if (Vector2.Distance(enemies[i].position, player.position + player.destOrigin) &lt; 320)
            	{
                		enemy.SetState(ChaserShip.States.CHASE);
            	}

            	if (enemy.GetState() == ChaserShip.States.CHASE)
            	{
                	Vector2 direction = (player.position + player.destOrigin) - enemy.position;
                	direction.Normalize();

                	float speed = 3;
                	enemy.body.velocity = direction * speed;

                	if (enemy.position.X + (enemy.destOrigin.X) &lt; player.position.X + (player.destOrigin.X))
                	{
                    	enemy.angle = enemy.angle - 5;
                	}
                	else
                	{
                    	enemy.angle = enemy.angle + 5;
                	}
            	}
        	}
    		}
	}

	if (enemies[i].position.Y > GraphicsDevice.Viewport.Height)
	{
    	enemies.Remove(enemies[i]);
	}
}

for (int i = 0; i &lt; explosions.Count; i++)
{
	explosions[i].Update(gameTime);

	if (explosions[i].sprite.isFinished())
	{
    	explosions.Remove(explosions[i]);
	}
}</pre>

We also want to add a collision check testing if each player laser has collided with an enemy:

<pre class="EnlighterJSRAW" data-enlighter-language="csharp" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">for (int i = 0; i &lt; playerLasers.Count; i++)
{
    bool shouldDestroyLaser = false;
    for (int j = 0; j &lt; enemies.Count; j++)
    {
        if (playerLasers[i].body.boundingBox.Intersects(enemies[j].body.boundingBox))
        {
            sndExplode[randInt(0, sndExplode.Count - 1)].Play();

            Explosion explosion = new Explosion(texExplosion, new Vector2(enemies[j].position.X, enemies[j].position.Y));
            explosion.scale = enemies[j].scale;

            Console.WriteLine("Shot enemy.  Origin: " + enemies[j].destOrigin + ", pos: " + enemies[j].position);

            explosion.position.Y += enemies[j].body.boundingBox.Height * 0.5f;
            explosions.Add(explosion);

            enemies.Remove(enemies[j]);

            shouldDestroyLaser = true;
        }
    }

    if (shouldDestroyLaser)
    {
        playerLasers.Remove(playerLasers[i]);
    }
}</pre>

Finally, we want to add some logic for the enemy spawn timer. &nbsp;We will be selecting a random enemy to spawn, then we add the instance to the enemies list. &nbsp;Add the following code to conclude our _UpdateGameplay_ method:

<pre class="EnlighterJSRAW" data-enlighter-language="csharp" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">// Enemy spawning
if (spawnEnemyTick &lt; spawnEnemyDelay)
{
	spawnEnemyTick++;
}
else
{
	Enemy enemy = null;
           	 
	if (randInt(0, 10) &lt;= 3)
	{
    	Vector2 spawnPos = new Vector2(randFloat(0, graphics.PreferredBackBufferWidth), -128);
    	enemy = new GunShip(texEnemies[0], spawnPos, new Vector2(0, randFloat(1, 3)));
	}
	else if (randInt(0, 10) >= 5)
	{
    	Vector2 spawnPos = new Vector2(randFloat(0, graphics.PreferredBackBufferWidth), -128);
    	enemy = new ChaserShip(texEnemies[1], spawnPos, new Vector2(0, randFloat(1, 3)));
	}
	else
	{
    	Vector2 spawnPos = new Vector2(randFloat(0, graphics.PreferredBackBufferWidth), -128);
    	enemy = new CarrierShip(texEnemies[2], spawnPos, new Vector2(0, randFloat(1, 3)));
	}

	enemies.Add(enemy);

	spawnEnemyTick = 0;
}</pre>

Now, we can move on to the _UpdateGameOver_ method! &nbsp;This method will be very similar to the _UpdateMainMenu_ method, but we’ll be dealing with the restart button instead of the play button. &nbsp;In the _UpdateGameOver_ method, add:

<pre class="EnlighterJSRAW" data-enlighter-language="csharp" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">if (restartButton.isActive)
{
	MouseState mouseState = Mouse.GetState();

	if (restartButton.boundingBox.Contains(mouseState.Position))
	{
    	if (mouseState.LeftButton == ButtonState.Pressed)
    	{
        	restartButton.SetDown(true);
        	restartButton.SetHovered(false);
    	}
    	else
    	{
        	restartButton.SetDown(false);
        	restartButton.SetHovered(true);
    	}

    	if (mouseState.LeftButton == ButtonState.Released && restartButton.lastIsDown)
    	{
        	changeGameState(GameState.Gameplay);
    	}
	}
	else
	{
    	restartButton.SetDown(false);
    	restartButton.SetHovered(false);
	}

	restartButton.lastIsDown = mouseState.LeftButton == ButtonState.Pressed ? true : false;
}
else
{
	restartButton.isActive = true;
}</pre>

Next, in the _resetGameplay_ method, we will be setting the player to not be dead, then reset the player position. &nbsp;In the _resetGameplay_ method, add the following:

<pre class="EnlighterJSRAW" data-enlighter-language="csharp" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">if (player != null)
{
	player.setDead(false);
	player.position = new Vector2((int)(graphics.PreferredBackBufferWidth * 0.5), (int)(graphics.PreferredBackBufferHeight * 0.5));
}</pre>

Then, in the _changeGameState_ method, we want to clear all of the lists of game objects, call _resetGameplay_, then change the state. &nbsp;Add the following to _changeGameState_:

<pre class="EnlighterJSRAW" data-enlighter-language="csharp" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">playButton.isActive = false;
restartButton.isActive = false;
explosions.Clear();
enemies.Clear();
playerLasers.Clear();
enemyLasers.Clear();
resetGameplay();

_gameState = gameState;</pre>

We have to make one quick addition to the _Draw_ method, which is to add the draw call for the scrolling background. &nbsp;Between the _spriteBatch.Begin_ call and the switch statement, let’s add this line:

<pre class="EnlighterJSRAW" data-enlighter-language="csharp" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">scrollingBackground.Draw(spriteBatch);</pre>

Now we can move on to the draw methods for our game states. &nbsp;Let’s start with the main menu. In the _DrawMainMenu_ method, add the following:

<pre class="EnlighterJSRAW" data-enlighter-language="csharp" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">string title = "SPACE SHOOTER";
spriteBatch.DrawString(fontArial, title, new Vector2(graphics.PreferredBackBufferWidth * 0.5f - (fontArial.MeasureString(title).X * 0.5f), graphics.PreferredBackBufferHeight * 0.2f), Color.White);

playButton.Draw(spriteBatch);</pre>

After that, in the _DrawGameplay_ method, add the following to draw each object in our lists of game objects:

<pre class="EnlighterJSRAW" data-enlighter-language="csharp" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">for (int i = 0; i &lt; enemies.Count; i++)
{
	enemies[i].Draw(spriteBatch);
}

for (int i = 0; i &lt; playerLasers.Count; i++)
{
	playerLasers[i].Draw(spriteBatch);
}

for (int i = 0; i &lt; enemyLasers.Count; i++)
{
	enemyLasers[i].Draw(spriteBatch);
}

for (int i = 0; i &lt; explosions.Count; i++)
{
	explosions[i].Draw(spriteBatch);
}

if (player != null)
{
	player.Draw(spriteBatch);
}</pre>

Finally, in the _DrawGameOver_ method, add the following to draw the elements on the game over game state:

<pre class="EnlighterJSRAW" data-enlighter-language="csharp" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">string title = "GAME OVER";
spriteBatch.DrawString(fontArial, title, new Vector2(graphics.PreferredBackBufferWidth * 0.5f - (fontArial.MeasureString(title).X * 0.5f), graphics.PreferredBackBufferHeight * 0.2f), Color.White);

restartButton.Draw(spriteBatch);</pre>

And that concludes this course! &nbsp;If you have any questions, comments, or general feedback, I’d love to hear it. &nbsp;You can email me at <jared.york@yorkcs.com>, or tweet me at [@jaredyork_][1].  


If you found this course valuable, and would like to receive news about future tutorials and courses we release, please fill out the [form][2].  


You can find the full source code for this course on [GitHub][3].

 [1]: https://twitter.com/jaredyork_
 [2]: https://forms.gle/tj2twZDEBH81A1vE9
 [3]: https://github.com/jaredyork/TutBuildSpaceShooterMonoGame