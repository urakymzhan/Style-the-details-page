---
Style the Details Page
---

## Style the details page

Follow the ideas from the presvious pages.

> [info]
>
> Create a new CSS file: `PLACESDetails.css`
>
> In `PLACESDetails.js` import your new stylesheet.

```JS
import './PLACESDetails.css'
```

>

I'm going to place the information on the left and the image on the right and divide the space in 1/3 and 2/3 proportion.

There are several pieces of information here:

- Title
- Description
- Hours
- Features
- geo coordinates

It would be nice to give each of these elements their own style. To do that you'll need to add some class names.

> [action]
>
> Edit `PLACESDetails.js`:

```JS
import { useParams } from "react-router-dom";
...

function PLACESDetails(props) {
  const { id } = useParams(); // Location index
  const { images, title, desc, hours, features, geo } = data[id];
  return (
    <div className="PLACESDetails">
      <div className="PLACESDetails-image">
        <img src={`${process.env.PUBLIC_URL}/images/${images[0]}`} />
      </div>
      <div className="PLACESDetails-info">
        <h1 className="PLACESDetails-title">{ title }</h1>
        <p className="PLACESDetails-desc">{ desc }</p>
        <p className="PLACESDetails-hours">{ hours }</p>
        <p className="PLACESDetails-features">
          {features.length > 0 &&
            features.map((feature, i) => (
              <span key={i}>
                [ {feature} ]
              </span>
          ))}

        </p>
        <p className="PLACESDetails-geo">{ geo.lat } { geo.lon }</p>
      </div>
    </div>
  )
}
```

>

Now add some styles for these elements.

> [action]
>
> Add the following to `PLACESDetails.css`

```css
.PLACESDetails {
  display: flex;
  flex-direction: row-reverse;
  width: 960px;
  min-height: 70vh; // temp fix
  margin: auto;
}
> .PLACESDetails .PLACESDetails-info {
  flex: 1;
  text-align: left;
  padding: 0 1em;
}
> .PLACESDetails .PLACESDetails-title {
  font-size: 2em;
  margin: 0;
}
> .PLACESDetails .PLACESDetails-image {
  flex: 2;
}
> .PLACESDetails .PLACESDetails-image img {
  width: 100%;
}
> .PLACESDetails .PLACESDetails-hours {
  font-size: 1.5em;
}
```

> The main container was given row-reverse to move the information to the left and the picture to the right. Since the image came first in the html it would have been on the left otherwise. Margin auto here centers the section by making the margins equal on the left and right side.

# Now Commit

> [action]

```bash
$ git add .
$ git commit -m 'style details page'
$ git push
```
