# svelte-tab-component

## Installation

1. Ensure you have node installed on your OS (v19 and above - recommended)
2. Navigate to the app where you would like to use the component and run the following in your terminal
```bash
npm install svelte-tab-component --save
```

## How to use the component

1. Inside the script tag of your .svelte file 
```javascript
import { Tabs } from 'svelte-tab-component'
```
2. Inside an HTML element use the imported Tabs component like so
```javascript
<Tabs {tabList} {role} initActive={'Tab 1'} on:setActiveTab={setActiveTabItem} /> 
```

## Props and handlers
1. ```{tabList}``` Required, An array of objects
2. ```{role}``` Optional, String
3. ```initActive={'Tab 1'}``` Optional, String
4. ```on:setActiveTab={setActiveTabItem}``` Required for handeling event from component, returns the Object associated with the selected tab

## Example
```+page.svelte```
```javascript
<script>
    import { Tabs } from 'svelte-tab-component'

    let tabList = [
    {
      label: "Tab 1",
      roles: ["Role 1", "Role 2", "Role 3", "Role 4"],
      extra: "stuff"
    },
    {
      label: "Tab 2",
      roles: ["Role 1", "Role 2"],
    },
    {
      label: "Tab 3",
      roles: ["Role 1", "Role 2", "Role 3"],
    },
    {
      label: "Tab 4",
      roles: ["Role 1", "Role 2", "Role 4"],
    },
    {
      label: "Tab 5",
      roles: ["Role 1", "Role 2", "Role 3", "Role 4"],
    },
  ];

  let role = "Role 1";

  let activeTab = "Tab 1"

  function setActiveTabItem(event) {
    console.log(event.detail.tabItem);
    activeTab = event.detail.tabItem.label
  }

</script>

<h1>Demo Tabs</h1>
<div>
    <div>
        <Tabs {tabList} {role} initActive={activeTab} on:setActiveTab={setActiveTabItem} />
    </div>

    <div>
        {#if activeTab === "Tab 1"}
          <div>
              <p>Tab 1 content goes here</p>
          </div>
        {:else if activeTab === "Tab 2"}
          <div>
              <p>Tab 2 content goes here</p>
          </div>
        {:else if activeTab === "Tab 3"}
          <div>
              <p>Tab 3 content goes here</p>
          </div>
        {:else if activeTab === "Tab 4"}
          <div>
              <p>Tab 4 content goes here</p>
          </div>
        {:else if activeTab === "Tab 5"}
          <div>
              <p>Tab 5 content goes here</p>
          </div>
        {/if}
    </div>
</div>

```


## Styling
Can be set with variables associated with every element
```css
--tabContainer-button-font-family
--tabContainer-button-padding
--tabContainer-button-color
--tabContainer-button-background
--tabContainer-button-border
--tabContainer-button-border-radius
--tabContainer-button-text-decoration
--tabContainer-button-width
--tabContainer-button-height
--tabContainer-button-text-align
--tabContainer-button-hover
--tabContainer-width
--tabContainer-ul-margin
--tabContainer-ul-padding
--tabContainer-ul-background-color
--tabContainer-ul-height
--tabContainer-ul-width
--tabContainer-ul-gap
--tabContainer-ul-justify-items
--tabContainer-ul-align-items
--tabContainer-ul-border-bottom
--tabContainer-ul-li-margin
--tabContainer-ul-li-padding
--tabContainer-ul-li-height
--tabContainer-ul-li-border-radius
--tabContainer-ul-li-button-color
--tabContainer-ul-li-button-margin
--tabContainer-ul-li-button-padding
--tabContainer-ul-li-button-height
--tabContainer-ul-li-button-border-radius
--tabContainer-ul-li-hover-background-color
--tabContainer-ul-li-button-active-color
--tabContainer-ul-li-button-active-background-color
--tabContainer-ul-li-button-active-border-bottom
--tabContainer-ul-li-button-active-margin-bottom
--tabContainer-ul-li-button-active-padding
```

## Feedback and recommendations
Please send me feedback or recommendations for improvements at mariusrossouwcr@gmail.com. I would love to here from you. [Donations](https://www.paypal.com/paypalme/MariusFRossouw) are welcome but not necessary.