# disasterbitch's Instagram post work skin

Here are some instructions on how to use my Instagram AO3 work skin. If you have any issues, first look at the [Troubleshooting section](#troubleshooting). If it doesn't help, feel free to:
* [Create an issue on this repository](https://github.com/disasterbitch/workskin-insta/issues) (this requires a GitHub account)
* [Leave a comment on the work skin on AO3](https://archiveofourown.org/works/95381476)
* [Message me on Threads](https://www.threads.com/@disasterbitchao3)

I created this work skin for [Easter Eggs](https://archiveofourown.org/works/88547306/), so go there if you want to see it in use, and all the HTML is on my [`fic-easter-eggs` repository](https://github.com/disasterbitch/fic-easter-eggs) if you want to see some HTML examples.

If you use this work skin, please credit me, and also let me know, I'd love to see what you make!

## Add the work skin to A03

To add the work skin to your AO3 account:
1. Go to your dashboard
1. Click **Skins** on the left
1. Click **My Work Skins**.
1. Click **Create Work Skin**. 
1. Add a title.
1. Copy the contents of [insta.css](insta.css).
1. Paste the CSS in the **CSS** box in AO3.

    **Important**: If you're using multiple work skins in the work, you have to add all the CSS in the same work skin, since you can only select one work skin per work. If you do that, make sure that none of the classes conflict, or you might have some issues. For more information, see [troubleshooting](#troubleshooting).

1. Click **Submit**.

To use the work skin in a work, edit the work and select the work skin you created from the **Select work skin** dropdown list.


## Write the HTML

To build your post, you can use the [HTML template](template.html). The sections below describe the different pieces of the work skin.

### Header

The header can contain:
* The user icon
* The username
* The verification icon
* A song

#### User icon

For the best result, the user icon should be a square.
From the template, replace `https://github.com/disasterbitch/workskin-insta/blob/main/?raw=true` with a direct link to your icon.

This also applies to user icons in [comments](#comments) and for the current user in the [footer](#footer).

#### Verification icon

The verification icon is added using this paragraph after any user name. You cna use the same one for the user posting and for the commenters:

```html
<p class="verified"><img class="verified" src="https://github.com/disasterbitch/workskin-insta/blob/main/instagram-icons/insta-verified.png?raw=true"></p>
```

### Post photo

For the best results, the post photo should have the 4:5 ratio. In the template, the image used in 1080px x 1350px.
You can add multiple images by adding more `<img>` in the paragraph in `<div class="pictures">`. You cna swipe left and right between pictures. 
Make sure to add all `<img>` tags in a single `<p>` and on the same line in your HTML, otherwise AO3 will wrap them in extra `<p>` tags and they will not display correctly. For example:

```html    
<div class="pictures">
    <p><img class="picture" src="https://github.com/disasterbitch/workskin-insta/blob/main/template-image.png"><img class="picture" src="https://github.com/disasterbitch/workskin-insta/blob/main/template-image.png"></p>
</div>
```

### Like

You can show a post as liked by the current user or not. This is controlled by the icon used:
* A post that is not liked uses `insta-likes.png`
* A liked post uses `insta-liked.png`

To change it, update the icon name in the link in the `<img>` tag:
```html
<p><img class="icon" src="https://github.com/disasterbitch/workskin-insta/blob/main/instagram-icons/insta-liked.png?raw=true"></p>
```

This also applies the like icon for each comment.

In the post, each icon has a `<p class="count">` paragraph where you can add the number of likes, comments, reposts, and shares.

### Caption

The caption is structured like this:

```html
<div class="captionBlock">
    <p class="caption"><span class="userName">username</span><span class="text">Caption text <span class="mention">@usermention</span> more caption text</span></p>
</div>
```

Don't add space after the `userName` span, the space is included in the CSS, but do add one before and after the `mention` span.

You can add multiple paragraphs to the caption, just keep some things in mind:
* To add a paragraph, just add a `<p class="caption"></p>` tag in the `<div class="captionBlock">` and write your text in it directly, don't use the `<span class="text">`.
* Writing a long/multi-paragraph caption will push the comment section down, which could cause some display issues on AO3 (I plan to fix that).

### Comments

#### Likes

#### Replies

### Footer

## Troubleshooting