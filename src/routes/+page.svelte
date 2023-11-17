

<script>
    import Tabs from "$lib/Tabs/Tabs.svelte";

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