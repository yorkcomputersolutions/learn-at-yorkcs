---
title: Build a Space Shooter with MonoGame – 5
author: Jared
type: post
date: 2019-05-20T21:56:18+00:00
url: /2019/05/20/build-a-space-shooter-with-monogame-5/
featured_image: /wp-content/uploads/2019/05/build-space-shooter-monogame-1.jpg
rank_math_internal_links_processed:
  - 1
rank_math_primary_category:
  - 1
rank_math_seo_score:
  - 60
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
  - 51
categories:
  - MonoGame
series:
  - Build a Space Shooter with MonoGame
tags:
  - 'C#'
  - cross-platform
  - crossplatform
  - crossplatform game
  - csharp
  - desktop
  - MonoGame
  - xna

---
The last two classes we’ll add will be devoted to the scrolling background system. &nbsp;Create a new class, and name it _ScrollingBackground.cs_. &nbsp;This class **does not** __need to inherit anything. &nbsp;It will still need the two usual using statements. &nbsp;We will want to add two fields containing background textures and layers:

{{<highlight cs>}}
private List<Texture2D> textures = new List<Texture2D>();
private List<ScrollingBackgroundLayer> layers = new List<ScrollingBackgroundLayer>();
{{</highlight>}}

The step is to add the constructor. &nbsp;We will be creating a vertical “stack” of three backgrounds, but we’ll be creating two more layers of backgrounds on top. &nbsp;This will allow us to have a buffer of backgrounds that will display as the layers before move off screen. This is how we can scroll the backgrounds. &nbsp;Let’s add the constructor:

{{<highlight cs>}}
public ScrollingBackground(List<Texture2D> textures)
{
	this.textures = textures;

	for (int i = -1; i < 2; i++) // position indexes
	{
    	for (int j = 0; j < 3; j++) { // 3 layers
        	Texture2D texture = textures[Game1.randInt(0, textures.Count - 1)];
        	Vector2 position = new Vector2(0, texture.Height * i);
        	Vector2 velocity = new Vector2(0, (j + 1) * 0.2f);
        	ScrollingBackgroundLayer layer = new ScrollingBackgroundLayer(this, texture, j, i, position, velocity);
        	layers.Add(layer);
    	}
	}
}
{{</highlight>}}

It’s time to add the more complicated part. &nbsp;Let’s first define our _Update_ method:

{{<highlight cs>}}
public void Update(GameTime gameTime) {


}
{{</highlight>}}

In the _Update_ method, the first thing we’ll want to do is sort each background by depth. &nbsp;We will then put the layer in the list of it’s corresponding depth. Add the following to start our _Update_ method:

{{<highlight cs>}}
List<ScrollingBackgroundLayer> layersDepth0 = new List<ScrollingBackgroundLayer>();
List<ScrollingBackgroundLayer> layersDepth1 = new List<ScrollingBackgroundLayer>();
List<ScrollingBackgroundLayer> layersDepth2 = new List<ScrollingBackgroundLayer>();
List<ScrollingBackgroundLayer> layersToReset = new List<ScrollingBackgroundLayer>();
       	 
for (int i = 0; i < layers.Count; i++)
{
	layers[i].Update(gameTime);

	switch (layers[i].depth)
	{
    	case 0:
        	{
            	layersDepth0.Add(layers[i]);
            	break;
        	}

    	case 1:
        	{
            	layersDepth1.Add(layers[i]);
            	break;
        	}

    	case 2:
        	{
            	layersDepth2.Add(layers[i]);
            	break;
        	}
	}
}
{{</highlight>}}

Next, we will have to iterate through each depth list and check if the first background is more than Y coordinate zero. &nbsp;We don’t want to run out of backgrounds so we will reset the position of each layer in the corresponding depth. Let’s add some more code to the _Update_ function:

{{<highlight cs>}}
bool resetLayersDepth0 = false;
bool resetLayersDepth1 = false;
bool resetLayersDepth2 = false;

// Loop through layers in depth 0
for (int i = 0; i < layersDepth0.Count; i++)
{
	if (layersDepth0[i].positionIndex == -1)
	{
    	if (layersDepth0[i].position.Y > 0)
    	{
        		resetLayersDepth0 = true;
    	}
	}
}

// Loop through layers in depth 1
for (int i = 0; i < layersDepth1.Count; i++)
{
	if (layersDepth1[i].positionIndex == -1)
	{
    	if (layersDepth1[i].position.Y > 0)
    	{
        	resetLayersDepth1 = true;
    	}
	}
}

// Loop through layers in depth 2
for (int i = 0; i < layersDepth2.Count; i++)
{
	if (layersDepth2[i].positionIndex == -1)
	{
    	if (layersDepth2[i].position.Y > 0)
    	{
        	resetLayersDepth2 = true;
    	}
	}
}

if (resetLayersDepth0)
{
	for (int i = 0; i < layersDepth0.Count; i++)
	{
    		layersDepth0[i].position = layersDepth0[i].initialPosition;
	}
}

if (resetLayersDepth1)
{
	for (int i = 0; i < layersDepth1.Count; i++)
	{
    		layersDepth1[i].position = layersDepth1[i].initialPosition;
	}
}

if (resetLayersDepth2)
{
	for (int i = 0; i < layersDepth2.Count; i++)
	{
    		layersDepth2[i].position = layersDepth2[i].initialPosition;
	}
}
{{</highlight>}}

Last, we will add the _Draw_ function, which will call the _Draw_ method of each layer:

{{<highlight cs>}}
public void Draw(SpriteBatch spriteBatch)
{
	for (int i = 0; i < layers.Count; i++)
	{
    		layers[i].Draw(spriteBatch);
	}
}
{{</highlight>}}

The last class we need to add will represent a scrolling background layer. &nbsp;Create a new class and call it _ScrollingBackgroundLayer.cs_. &nbsp;This class will need to extend _Entity_. &nbsp;Make sure to add the two usual using statements. We will also have to add several fields:

{{<highlight cs>}}
private ScrollingBackground scrollingBackground;
private Texture2D texture;
public Texture2D getTexture() { return texture; }
public int depth = 0;
public int positionIndex = 0;
public Vector2 initialPosition;
{{</highlight>}}

Let’s add the following constructor:

{{<highlight cs>}}
public ScrollingBackgroundLayer(ScrollingBackground scrollingBackground, Texture2D texture, int depth, int positionIndex, Vector2 position, Vector2 velocity) : base()
{
	this.scrollingBackground = scrollingBackground;
	this.texture = texture;
	this.depth = depth;
	this.positionIndex = positionIndex;
	this.position = position;
	initialPosition = this.position;
	body.velocity = velocity;
}
{{</highlight>}}

Then we will need to add the usual _Update_ method:

{{<highlight cs>}}
public new void Update(GameTime gameTime)
{
	base.Update(gameTime);
}
{{</highlight>}}

Finally, we’ll add the _Draw_ method, which will draw the background layer when called:

{{<highlight cs>}}
public void Draw(SpriteBatch spriteBatch)
{
	spriteBatch.Draw(texture, position, Color.White);
}
{{</highlight>}}

Let&#8217;s move on to [part six][1] where we finish up our game.

 [1]: https://learn.yorkcs.com/2019/05/20/build-a-space-shooter-with-monogame-6/