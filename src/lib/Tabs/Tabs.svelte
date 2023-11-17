<script>
    import { createEventDispatcher } from "svelte";
    /*
        Receive the props
    */
    export let tabList = [];
    export let role = "ALL";
    export let initActive = "";
    let tabIsActive = initActive;

    const dispatch = createEventDispatcher();

    /*
        We set and dispatch the new active tabItem
    */
    function setActive(tabItem) {
        tabIsActive = tabItem.label;

        dispatch("setActiveTab", {
            tabItem,
        });
    }
</script>

<div class="tabContainer">
    <ul>
        {#each tabList as tabItem, index (tabItem.label)}
            {#if (tabItem.roles && tabItem.roles.includes(role)) || role === "ALL"}
                <!-- <TabItem {tabItem} {index} on:newActiveTabItem={setActive} /> -->
                <li class:active={tabIsActive === tabItem.label}>
                    <button
                        on:click={() => {
                            setActive(tabItem);
                        }}
                    >
                        <h4>
                            <!-- 
                                Check is label is provided
                            -->
                            {#if tabItem.label}
                                {tabItem.label}
                            {:else}
                                No Label Provided
                            {/if}
                        </h4>
                    </button>
                </li>
            {/if}
        {/each}
    </ul>
</div>

<!-- Keyboard Accessibility: Ensure that tabs can be navigated using keyboard controls (like arrow keys), which is a core aspect of accessibility. Using "buttons" adds usability by making the tabs selectable using a keyboard -->

<style>
    button {
        font-family: var(--tabContainer-button-font-family, Roboto Light, Roboto bold, system-ui, -apple-system,
            BlinkMacSystemFont, "Helvetica Neue", sans-serif);
        padding: var(--tabContainer-button-padding, none);
        color: var(--tabContainer-button-color, inherit);
        background: var(--tabContainer-button-background, transparent);
        border: var(--tabContainer-button-border, none);
        border-radius: var(--tabContainer-button-border-radius, none);
        text-decoration: var(--tabContainer-button-text-decoration, none);
        width: var(--tabContainer-button-width, auto);
        height: var(--tabContainer-button-height, auto);
        text-align: var(--tabContainer-button-text-align, left);
    }

    button:hover {
        cursor: var(--tabContainer-button-hover, pointer);
    }
    .tabContainer {
        width: var(--tabContainer-width, 100%);
    }

    .tabContainer ul {
        list-style-type: none;
        margin: var(--tabContainer-ul-margin, 0);
        padding: var(--tabContainer-ul-padding, 0);
        background-color: var(--tabContainer-ul-background-color, transparent);
        height: var(--tabContainer-ul-height, fit-content);
        width: var(--tabContainer-ul-width, 100%);
        display: flex;
        flex-direction: row;
        gap: var(--tabContainer-ul-gap, 8px);
        justify-items: var(--tabContainer-ul-justify-items, flex-start);
        align-items: var(--tabContainer-ul-align-items, center);
        border-bottom: var(--tabContainer-ul-border-bottom, 2px solid #ddd);
    }
    .tabContainer ul li {
        display: flex;
        flex-direction: row;
        justify-items: stretch;
        margin: var(--tabContainer-ul-li-margin, 0);
        padding: var(--tabContainer-ul-li-padding, 0);
        height: var(--tabContainer-ul-li-height, auto);
        border-radius: var(--tabContainer-ul-li-border-radius, 4px 4px 0px 0px);
    }
    .tabContainer ul li button {
        color: var(--tabContainer-ul-li-button-color, #95979f);
        display: flex;
        flex-direction: row;
        justify-items: stretch;
        margin: var(--tabContainer-ul-li-button-margin, 0);
        padding: var(--tabContainer-ul-li-button-padding, 0px 10px 0px 10px);
        height: var(--tabContainer-ul-li-button-height, auto);
        border-radius: var(
            --tabContainer-ul-li-button-border-radius,
            4px 4px 0px 0px
        );
    }
    .tabContainer ul li:hover {
        background-color: var(
            --tabContainer-ul-li-hover-background-color,
            #ecedf1
        );
    }

    .tabContainer ul li.active button {
        color: var(--tabContainer-ul-li-button-active-color, #222);
        background-color: var(
            --tabContainer-ul-li-button-active-background-color,
            #ecedf1
        );
        border-bottom: var(
            --tabContainer-ul-li-button-active-border-bottom,
            4px solid dodgerblue
        );
        margin-bottom: var(
            --tabContainer-ul-li-button-active-margin-bottom,
            -2px
        );
        padding: var(
            --tabContainer-ul-li-button-active-padding,
            0px 10px 0px 10px
        );
    }
</style>
