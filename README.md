# disasterbitch's Instagram post work skin

Here are some instructions on how to use my Instagram AO3 work skin. If you have any issues, first look at the [Troubleshooting section](#troubleshooting). If it doesn't help, feel free to:
* [Create an issue on this repository](https://github.com/disasterbitch/workskin-insta/issues) (this requires a GitHub account)
* [Leave a comment on the work skin on AO3](https://archiveofourown.org/works/95381476)
* [Message me on Threads](https://www.threads.com/@disasterbitchao3)

You can also use these to request improvements or new options. I can't guarantee I'll do it, but I'll definitely consider it. Just make sure that you request isn't already listed in the [issues](https://github.com/disasterbitch/workskin-insta/issues).

I created this work skin for [Easter Eggs](https://archiveofourown.org/works/88547306/), so go there if you want to see it in use, and all the HTML is on my [`fic-easter-eggs` repository](https://github.com/disasterbitch/fic-easter-eggs) if you want to see some HTML examples.

If you use this work skin, please credit me, and also let me know, I'd love to see what you make!

Finally, if you want to contribute to this work skin, you can open a pull request! Just make sure to let me know how you would like to be credited.

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
From the template, replace `https://disasterbitch.github.io/workskin-insta/template-icon.png` with a direct link to your icon.

This also applies to user icons in [comments](#comments) and for the current user in the [footer](#footer).

#### Verification icon

The verification icon is added using this paragraph after any user name. You cna use the same one for the user posting and for the commenters:

```html
<p class="verified"><img class="verified" src="https://disasterbitch.github.io/workskin-insta/instagram-icons/insta-verified.png"></p>
```

#### Song

You can add a song to a post using this block in the header:

```html
<div class="song">
    <p><a href="">♫ Artist · Title</a></p>
</div>
```

In `href=""`, you can add a link to the song. if you don't need it, remove the `<a></a>` tag and just add the artist and title directly in the `<p>`.

This block should be added in the `<div class="header">` block, under the user block.


### Post photo

For the best results, the post photo should have the 4:5 ratio. In the template, the image used in 1080px x 1350px.
You can add multiple images by adding more `<img>` in the paragraph in `<div class="pictures">`. You cna swipe left and right between pictures. 
Make sure to add all `<img>` tags in a single `<p>` and on the same line in your HTML, otherwise AO3 will wrap them in extra `<p>` tags and they will not display correctly. For example:

```html    
<div class="pictures">
    <p><img class="picture" src="https://disasterbitch.github.io/workskin-insta/template-image.png"><img class="picture" src="https://disasterbitch.github.io/workskin-insta/template-image.png"></p>
</div>
```

### Like

You can show a post as liked by the current user or not. This is controlled by the icon used:
* A post that is not liked uses `insta-likes.png`
* A liked post uses `insta-liked.png`

To change it, update the icon name in the link in the `<img>` tag:
```html
<p><img class="icon" src="https://disasterbitch.github.io/workskin-insta/instagram-icons/insta-liked.png"></p>
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

This work skin allows you to have an interactive comment section. You can open the comments by clicking anywhere on the post image, the icons under the post, or the caption. You can then close the comments by clicking the image above the comment section.

Due to AO3's HTML restrictions I couldn't make only the comments icon clickable (or at least I couldn't figure out how). I could have just made the icons clickable, but that would have made it impossible to close the comments, since the icons are hidden by the comment section.

Each comment, whether it's a top-level comment or a [reply](#replies), is structured like this:
```html
<div class="instaComment">
    <p class="userIcon"><img class="userIcon" src="https://disasterbitch.github.io/workskin-insta/template-icon.png"></p>
    <p class="userName">username</p>
    <p class="timestamp">1h</p>
    <p class="commentLikeIcon"><img class="icon" src="https://disasterbitch.github.io/workskin-insta/instagram-icons/insta-likes.png"><span class="commentLikeCount d4">1000</span></p>
    <p class="text">Comment text</p>
    <p class="reply">Reply</p>
</div>   
```

The same [user icon](#user-icon) and [like](#like) icon instructions described in previous sections apply here too. 

#### Likes

When I created this work skin, I had some difficulties aligning the number of likes for a comment under the like icon. To fix this issue, I had to add a class that indicates the number of digits for the like count and customize the spacing based on that number. This is a bit annoying, but it's the only solution I have for now. 

In the `commentLikeCount` span, add the relevant class, from `d1` for a single-digit like count, to `d4` for a four-digit like count. There is an example of each in the template.

#### Replies

To add replies to a comment, add the following block inside the `<div class="instaComment">`:

```html
<details class="moreReplies">
    <summary class="reply"></summary>                       
    <div class="instaComment">
        <p class="userIcon"><img class="userIcon" src="https://disasterbitch.github.io/workskin-insta/template-icon.png"></p>
        <p class="userName">username</p>
        <p class="timestamp">7m</p>
        <p class="commentLikeIcon"><img class="icon" src="https://disasterbitch.github.io/workskin-insta/instagram-icons/insta-likes.png"><span class="commentLikeCount d2">10</span></p>
        <p class="text">Reply text</p>
        <p class="reply">Reply</p>
    </div>
</details>
```

It should be after `<p class="reply">Reply</p>` and before the closing `</div>`.

To add multiple replies, just add as many `<div class="instaComment">` blocks as needed. Don't repeat the `<details class="moreReplies">` tag. The template has an example of a comment with multiple replies.

#### Footer

The footer of the comments section contains the form for the current user to leave a comment. You just need to add an icon for the user.

You can also customize the list of emojis to display.

### Post date

At the bottom of the HTML, you can customize the date of the post:

```html
<div class="timestamp">
    <p>October 25</p>
</div>
```

## Troubleshooting

If you have any spacing/display issues, check the following.

### Blank lines

Make sure that your HTML doesn't have any blank lines between elements. 

If there are any, AO3 will add an empty `<p></p>`, which might mess with the display. Check your post for this block and remove it.

### Conflicting CSS

If you're using other work skins in the same fic, make sure that the CSS classes don't conflict with the ones in this work skin. 

For example, another work skin might define CSS for the `.comments`, which are different from the ones in [insta.css](insta.css). To avoid this, make sure that other work skins include a top-lever container (like `<div class="instagram">` here), and that all the CSS rules are prefixed with the class for that container (in this example, `.instagram`). 

### Broken icons

Unfortunately GitHub can be unreliable and sometimes the images can break. It usually returns to normal pretty quickly, but keep this in mind. If the icons from the template don't work:
* Check that they still exist under the `instagram-icons` folder.
* Check if there is currently a [GitHub outage](https://www.githubstatus.com/).

You can also save the icons and host them yourself if you don't want to depend on this repository.