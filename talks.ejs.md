```{=html}
<%
const sections = [
  ["invited", "Invited Research Talks"],
  ["contributed", "Contributed Research Talks"],
  ["expository", "Expository and Workshop Talks"],
  ["attended", "Selected Conferences and Programs"]
];

for (const [key, heading] of sections) {
  const group = items.filter(item => item.section === key);
  if (group.length === 0) continue;
%>

<section class="talk-section">
  <h2><%= heading %></h2>

  <% if (key === "attended") { %>
    <p class="talk-section-description">
      The following are selected conferences, workshops, and programs in which I participated without giving a talk.
    </p>
  <% } %>

  <div class="talk-list">

    <% for (const item of group) { %>

      <div class="talk-entry">

        <span class="talk-conference">
          <a href="<%- item.url %>"><strong><%= item.conference %></strong></a>,
        </span>

        <span class="talk-meta">
          <span class="talk-location"><%= item.location %>,</span>
          <span class="talk-date"><%= item.dates %></span>
        </span>

        <% if (item["talk-title"]) { %>
          <div class="talk-title">
            <em><%= item["talk-title"] %></em>
          </div>
        <% } %>

        <% if (item.note) { %>
          <div class="talk-note">
            <%= item.note %>
          </div>
        <% } %>

      </div>

    <% } %>

  </div>
</section>

<%
}
%>
```