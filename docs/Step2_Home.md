# Home component

In this step we will make use of ```ui5-card``` as main building block for our home view. We will create the "Featured" section. As you can see below, it consists of two "cards" - "Inventory" and "Security". Each of them has a header and content section with a list of important information.

![Alt text](./step2.png?raw=true "Home")


1. Import the `ui5-card` (and other components) in `src/home/index.jsx`.

```js 
  import "@ui5/webcomponents/dist/Card";
  import "@ui5/webcomponents/dist/Title";
  import "@ui5/webcomponents/dist/Label";
  import "@ui5/webcomponents/dist/List";
  import "@ui5/webcomponents/dist/CustomListItem";
  import "@ui5/webcomponents/dist/StandardListItem";
```

2. Let's start with the "Featured" section.
Add a `ui5-title` to the page with heading level 3 and "Featured" text

```js
  const Home = () => {
    return (
      <div className="app-content">
        <ui5-title level="H3">Featured</ui5-title>
      </div>
    );
  };
```

3. Now, let's add the `ui5-card`. We will also use `ui5-list` (List) and `ui5-li` (StandardListItem) for the `ui5-card` content. 
You can get familiar with the API of those components - [Card API](https://sap.github.io/ui5-webcomponents/playground/components/Card/) and [List API](https://sap.github.io/ui5-webcomponents/playground/components/List/). What is going below?
We are just using the API of the UI5 WebComponents ("heading", "subtitle" and "status") and the JSX syntax to map the data and the cards will render nicely.

```html
  <div className="app-content">
    <ui5-title level="H3">Featured</ui5-title>
    <section className="section">
      {data.featured.map((dataObj) =>
        <ui5-card
          key={dataObj.key}
          heading={dataObj.heading}
          subtitle={dataObj.subtitle}
          status={dataObj.status}
          class="ui5card">

          <ui5-list separators="Inner" className="list-item">
            {dataObj.items.map(item =>
              <ui5-li
                key={item.key}
                icon={item.icon}
                description={item.description}
                info={item.info}
                info-state={item.infoState}
                class="ui5list-item">{item.title}</ui5-li>
            )}
          </ui5-list>
        </ui5-card>
      )}
    </section>
  </div>
```

4. The layouting and ordering of the cards is responsibility of the app developer. To help you focus on the work with web components we created the needed layouting in `styles.css` file next to `index.jsx`. Nothing magical, we make use of `display:flex` for the layouting and setting some `min-width` to the `ui5-card`.

Import the css file by calling:
```js
import "./styles.css"
```

9. You can copy the rest of the sections in the `Home` component from [Sources of Smart Store (Home.js)](https://github.com/ilhan007/ui5con-app/blob/master/src/home/Home.js), but don`t forget to copy all the UI5 components imports from the [Sources of Smart Store (App.js)](https://github.com/ilhan007/ui5con-app/blob/master/src/App.js) as some of them are used in these cards.

### [Step #3 - Events and Routing](./Step3_Events_and_Routing.md)