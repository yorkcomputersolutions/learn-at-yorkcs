---
title: Build a Space Shooter with MonoGame – 4
author: Jared
type: post
date: 2019-05-20T23:02:44+00:00
url: /2019/05/20/build-a-space-shooter-with-monogame-4/
featured_image: /wp-content/uploads/2019/05/build-space-shooter-monogame-1.jpg
rank_math_internal_links_processed:
  - 1
rank_math_primary_category:
  - 184
rank_math_seo_score:
  - 21
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
  - 47
categories:
  - MonoGame
series:
  - Build a Space Shooter with MonoGame
tags:
  - 'C# game'
  - csharp game
  - MonoGame

---
Next let’s create a new class named _Entity.cs_. &nbsp;The player spaceship and any other enemies in the game with inherit the properties of this class. &nbsp;In our new _Entity_ class, add a using statement for _Microsoft.Xna.Framework_. &nbsp;Every entity will store the following information: is rotatable, scale, position, source origin, destination origin, and physics body. &nbsp;Add the following to initialize these fields and properties:

{{<highlight cs>}}
protected bool isRotatable = false;
public Vector2 scale = new Vector2(1.5f, 1.5f);
public Vector2 position = new Vector2(0, 0);
protected Vector2 sourceOrigin = new Vector2(0, 0);
public Vector2 destOrigin = new Vector2(0, 0);
public PhysicsBody body { get; set; }
{{</highlight>}}

Let’s add our constructor, then instantiate a physics body inside it. &nbsp;In other words, when another class inherits this _Entity_ class, a physics body will automatically be created for that class. &nbsp;It will all make sense shortly since it can be a bit confusing. Add the following to add our constructor:

{{<highlight cs>}}
public Entity() {
	body = new PhysicsBody();
}
{{</highlight>}}

We will also want a way to set up the bounding box for our entities. &nbsp;Add the following method:

{{<highlight cs>}}
public void setupBoundingBox(int width, int height)
{
	body.boundingBox = new Rectangle((int)(position.X - destOrigin.X), (int)(position.Y - destOrigin.Y), (int)(width * scale.X), (int)(height * scale.Y));
}
{{</highlight>}}

Finally, we will need to add an _Update_ method. &nbsp;This method will be called for every entity. &nbsp;Let’s add the _Update_ method:

{{<highlight cs>}}
public void Update(GameTime gameTime)
{
	if (body != null)
	{
    	position.X += body.velocity.X;
    	position.Y += body.velocity.Y;

    	body.boundingBox = new Rectangle((int)position.X - (int)destOrigin.X, (int)position.Y - (int)destOrigin.Y, body.boundingBox.Width, body.boundingBox.Height);

	}
	else
	{
    	Console.WriteLine("[BaseEntity] body not found, skipping position updates.");
	}
}
{{</highlight>}}

Our _Entity_ class is finished! &nbsp;The next step is to add a new class named _PhysicsBody.cs_. &nbsp;This class will contain no constructor or any other methods. &nbsp;We will just be adding two fields: _velocity_, and _boundingBox_. &nbsp;But first, we will need to add a using statement pointing to _Microsoft.Xna.Framework_. &nbsp;After that, add the following code to specify our two fields:

{{<highlight cs>}}
public Vector2 velocity = new Vector2(0, 0);
public Rectangle boundingBox;
{{</highlight>}}

Boom. &nbsp;We are done with the _PhysicsBody_ class. &nbsp;Next, let’s create another class called _Enemy.cs_. &nbsp;This class will be inheriting the _Entity_ class. &nbsp;Then, any enemy spaceship class will inherit from this _Enemy_ class. &nbsp;Let’s add _using Microsoft.Xna.Framework;_ and _using Microsoft.Xna.Framework.Graphics;_ to our using statements. The _Enemy_ class will hold an instance of a _Texture2D_, an _AnimatedSprite_, and a float containing the angle.  


Now we can add our couple fields and property:

{{<highlight cs>}}
protected Texture2D texture;
protected AnimatedSprite sprite;
public float angle { get; set; }
{{</highlight>}}

Note, the next chunk of code isn’t your average constructor. &nbsp;Write the following:

{{<highlight cs>}}
public Enemy(Texture2D texture, Vector2 position, Vector2 velocity) : base()
{
	this.texture = texture;
	sprite = new AnimatedSprite(this.texture, 16, 16, 10);
	scale = new Vector2(Game1.randFloat(10, 20) * 0.1f);
	sourceOrigin = new Vector2(sprite.frameWidth * 0.5f, sprite.frameHeight * 0.5f);
	destOrigin = new Vector2((sprite.frameWidth * 0.5f) * scale.X, (sprite.frameHeight * 0.5f) * scale.Y);
	this.position = position;
	body.velocity = velocity;

	setupBoundingBox(sprite.frameWidth, sprite.frameHeight);
}
{{</highlight>}}

Perhaps you notice the “: base()” after the ending parenthesis. &nbsp;You would normally put in the requirements required by the _Entity_ class, but there are none, so we’ll leave it empty. &nbsp;We will also have to change the class declaration from:  


_class Enemy  
_ 

To:  


_class Enemy : Entity  
_ 

This is what tells the compiler that we want our _Enemy_ class to extend _Entity_. &nbsp;After our constructor, let’s add an _Update_ method. &nbsp;Every tick, we will be setting the destination origin and update the animated sprite. &nbsp;Further, we will also be calling the _Update_ method of the _Entity_ class. &nbsp;We can accomplish that by utilizing _base.Update(gameTime)_. &nbsp;Let’s add this method:

{{<highlight cs>}}
public new virtual void Update(GameTime gameTime)
{
	destOrigin = new Vector2(
    	(float)Math.Round((sprite.frameWidth * 0.5f) * scale.X),
    	(float)Math.Round((sprite.frameHeight * 0.5f) * scale.Y)
	);

	sprite.Update(gameTime);

	base.Update(gameTime);
}
{{</highlight>}}

We will also add a _Draw_ method, which will be called if any enemy spaceship class extending this class does not have it’s own _Draw_ method:

{{<highlight cs>}}
public virtual void Draw(SpriteBatch spriteBatch)
{
	if (isRotatable)
	{
    	Rectangle destRect = new Rectangle((int)position.X, (int)position.Y, (int)(sprite.frameWidth * scale.X), (int)(sprite.frameHeight * scale.Y));
    	spriteBatch.Draw(texture, destRect, sprite.sourceRect, Color.White, MathHelper.ToRadians(angle), sourceOrigin, SpriteEffects.None, 0);

	}
	else
	{
    	Rectangle destRect = new Rectangle((int)position.X, (int)position.Y, (int)(sprite.frameWidth * scale.X), (int)(sprite.frameHeight * scale.Y));
    	spriteBatch.Draw(texture, destRect, sprite.sourceRect, Color.White, MathHelper.ToRadians(angle), sourceOrigin, SpriteEffects.None, 0);
	}
}
{{</highlight>}}

Next, we will add our three enemy classes. &nbsp;We will start with a new class named, _GunShip_. &nbsp;In this new class, let’s make this class extend _Entity_ by changing our class declaration to:  


_class GunShip : Enemy  
_ 

Before we continue, let’s not forget to add two using statements like so:  


_using Microsoft.Xna.Framework;_

_using Microsoft.Xna.Framework.Graphics;  
_ 

Now let’s add three fields to store the shoot delay, the shoot tick, and whether or not the gun ship can shoot:

{{<highlight cs>}}
private int shootDelay = 60;
private int shootTick = 0;
public bool canShoot = false;
{{</highlight>}}

Then, let’s add the constructor, as well as provide the arguments to instantiate the _Enemy_ class we’re inheriting:

{{<highlight cs>}}
public GunShip(Texture2D texture, Vector2 position, Vector2 velocity) : base(texture, position, velocity)
{
       	 
}
{{</highlight>}}

Every tick, we want to update our shoot timer and the animated sprite. &nbsp;To accomplish, let’s add the following _Update_ method:

{{<highlight cs>}}
public override void Update(GameTime gameTime)
{
	if (!canShoot)
	{
    	if (shootTick < shootDelay)
    	{
        	shootTick++;
    	}
    	else
    	{
        	canShoot = true;
    	}
	}

	sprite.Update(gameTime);

	base.Update(gameTime);
}
{{</highlight>}}

Finally, we will want to add a method to reset our shoot fields, once this gun ship has shot a laser. &nbsp;Let’s add the following method and call it _resetCanShoot_:

{{<highlight cs>}}
public void resetCanShoot()
{
	canShoot = false;
	shootTick = 0;
}
{{</highlight>}}

Now that the _GunShip_ class is defined, we can add a new class named _ChaserShip.cs_. &nbsp;For the chaser ship, we want to check if the player is within a specified distance, then have the chaser ship chaser after the player. &nbsp;By now, you should know what to do in order to make this class inherit _Enemy_. Add the following using statements before we forget:  


_using Microsoft.Xna.Framework;_

_using Microsoft.Xna.Framework.Graphics;  
_ 

To start creating the state system for our _ChaserShip_ class, let’s define a enum with two values:

{{<highlight cs>}}
public enum States
{
	MOVE_DOWN,
	CHASE
}
{{</highlight>}}

After that, let’s set the current state by creating a _state_ field:

{{<highlight cs>}}
private States state = States.MOVE_DOWN;
{{</highlight>}}

Let’s add two methods to set and retrieve the state property:

{{<highlight cs>}}
public void SetState(States state)
{
	this.state = state;
	isRotatable = true;
}

public States GetState()
{
	return state;
}
{{</highlight>}}

Now we can add our constructor, we’ll provide the arguments to the _Enemy_ class as usual. &nbsp;We will also set the _angle_ to __:

{{<highlight cs>}}
public ChaserShip(Texture2D texture, Vector2 position, Vector2 velocity) : base(texture, position, velocity)
{
	angle = 0;
}
{{</highlight>}}

We will also want to add our _Update_ method that will call the _Update_ method of _Enemy_:

{{<highlight cs>}}
public override void Update(GameTime gameTime)
{
	base.Update(gameTime);
}
{{</highlight>}}

The last class we are adding that inherits _Enemy_ is _CarrierShip_. &nbsp;Add a new class and name it _CarrierShip.cs_, add the two usual using statements, and make this new class inherit _Enemy_. &nbsp;The _CarrierShip_ really doesn’t do anything special actually. &nbsp;We will just be taking arguments in and passing them to the _Enemy_ class. &nbsp;Add the following code for our constructor:

{{<highlight cs>}}
public CarrierShip(Texture2D texture, Vector2 position, Vector2 velocity) : base(texture, position, velocity)
{
       	 
}
{{</highlight>}}

That’s it for the _CarrierShip_ class. &nbsp;While we’re at it, let’s add a new class for enemy lasers. &nbsp;Name this new class, _EnemyLaser.cs_. &nbsp;Add the usual using statements, and make the class extend _Entity_. &nbsp;We will need to add a field to store the texture:

{{<highlight cs>}}
private Texture2D texture;

Let’s add our constructor:

public EnemyLaser(Texture2D texture, Vector2 position, Vector2 velocity) : base()
{
	this.texture = texture;
	this.position = position;
	body.velocity = velocity;

	setupBoundingBox(this.texture.Width, this.texture.Height);
}
{{</highlight>}}

As I mentioned previously, _Entity_ doesn’t accept any arguments, so we don’t need to provide any arguments within the _base_ keyword. &nbsp;We will also add an _Update_ method, which will call the _Update_ method of _Entity_:

{{<highlight cs>}}
public new void Update(GameTime gameTime)
{
        	base.Update(gameTime);
}
{{</highlight>}}

We will conclude writing this class by adding a _Draw_ method:

{{<highlight cs>}}
public void Draw(SpriteBatch spriteBatch)
{
	spriteBatch.Draw(texture, position, Color.White);
}
{{</highlight>}}

Let’s create a new class for the player’s laser and name it _PlayerLaser.cs_. &nbsp;Add the two using statements, then make the class inherit _Entity_. &nbsp;Add a field for storing the texture:  


_private Texture2D texture;  
_ 

After that we can add the constructor:

{{<highlight cs>}}
public PlayerLaser(Texture2D texture, Vector2 position, Vector2 velocity) : base()
{
	this.texture = texture;
	this.position = position;
	body.velocity = velocity;

	setupBoundingBox(this.texture.Width, this.texture.Height);
}
{{</highlight>}}

Then we can add our _Update_ and _Draw_ methods respectively:

{{<highlight cs>}}
public new void Update(GameTime gameTime)
{
	base.Update(gameTime);
}

public void Draw(SpriteBatch spriteBatch)
{
	spriteBatch.Draw(texture, position, Color.White);
}
{{</highlight>}}

The next class we will add is the _Player_ class. &nbsp;Add a new class and name it _Player.cs_. &nbsp;Add the using statements, and make the class extend _Entity_. &nbsp;This class will store a texture, an animated sprite, the movement speed, and a property storing whether or not the player is dead.  


Add the following code to create these fields and properties:

{{<highlight cs>}}
public Texture2D texture;
public AnimatedSprite sprite;
public float moveSpeed = 4;
private bool _dead = false;
public bool isDead() { return _dead; }
public void setDead(bool isDead) { _dead = isDead; }
{{</highlight>}}

After that, let’s create the constructor:

{{<highlight cs>}}
public Player(Texture2D texture, Vector2 position) : base()
{
	this.texture = texture;
	sprite = new AnimatedSprite(this.texture, 16, 16, 10);
	this.position = position;
	sourceOrigin = new Vector2(sprite.frameWidth * 0.5f, sprite.frameHeight * 0.5f);
	destOrigin = new Vector2((sprite.frameWidth * 0.5f) * scale.X, (sprite.frameHeight * 0.5f) * scale.Y);
	setupBoundingBox(sprite.frameWidth, sprite.frameHeight);
}
{{</highlight>}}

Now that we added our constructor, we will need to define four methods we will use for movement:

{{<highlight cs>}}
public void MoveUp()
{
	body.velocity.Y = -moveSpeed;
}

public void MoveDown()
{
	body.velocity.Y = moveSpeed;
}

public void MoveLeft()
{
	body.velocity.X = -moveSpeed;
}

public void MoveRight()
{
	body.velocity.X = moveSpeed;
}
{{</highlight>}}

Next, we’ll add the _Update_ function which will update the animated sprite, and call the base _Update_ function of _Entity_:

{{<highlight cs>}}
public void Update(GameTime gameTime)
{
	sprite.Update(gameTime);

	base.Update(gameTime);
}
{{</highlight>}}

Finally, we will finish the _Player_ class by adding the _Draw_ method:

{{<highlight cs>}}
public void Draw(SpriteBatch spriteBatch)
{
	if (!_dead)
	{
    	Rectangle destRect = new Rectangle((int)position.X, (int)position.Y, (int)(sprite.frameWidth * scale.X), (int)(sprite.frameHeight * scale.Y));
    	spriteBatch.Draw(texture, destRect, sprite.sourceRect, Color.White);
	}
}
{{</highlight>}}

We only want to draw the player if the player is not dead. &nbsp;The player instance won’t actually be destroyed, but we’ll fake it by making it invisible when it’s hit.  


Next we will create a class for explosions. &nbsp;Name this new class, _Explosion.cs_ and make it extend _Entity_. &nbsp;Also add the usual two using statements. &nbsp;This class will contain three fields: _texture_, _sprite_, __and _origin_. &nbsp;Let’s add them!

{{<highlight cs>}}
private Texture2D texture;
public AnimatedSprite sprite;
public Vector2 origin;
{{</highlight>}}

Then let’s add the constructor:

{{<highlight cs>}}
public Explosion(Texture2D texture, Vector2 position) : base()
{
	this.texture = texture;
	sprite = new AnimatedSprite(this.texture, 32, 32, 5);
	sprite.setCanRepeat(false);
	this.position = position;
	origin = new Vector2((sprite.frameWidth * 0.5f) * scale.X, (sprite.frameHeight * 0.5f) * scale.Y);
	setupBoundingBox(sprite.frameWidth, sprite.frameHeight);
}
{{</highlight>}}

We can also add the _Update_ method:

{{<highlight cs>}}
public new void Update(GameTime gameTime)
{
	sprite.Update(gameTime);

	base.Update(gameTime);
}
{{</highlight>}}

Let’s finally add the _Draw_ method:

{{<highlight cs>}}
public void Draw(SpriteBatch spriteBatch)
{
	Rectangle destRect = new Rectangle((int)position.X - (int)origin.X, (int)position.Y - (int)origin.Y, (int)(sprite.frameWidth * scale.X), (int)(sprite.frameHeight * scale.Y));
	spriteBatch.Draw(texture, destRect, sprite.sourceRect, Color.White);
}
{{</highlight>}}

Next it&#8217;s time to go on to [part five][1]!

 [1]: https://learn.yorkcs.com/2019/05/20/build-a-space-shooter-with-monogame-5/