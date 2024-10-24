---
title: "Workout Descriptions"
description: "Explore all the workout exercises in the Stickie method. Filter by arms, legs, or abs to find personalized exercises for your fitness goals."
layout: "workout-descriptions"
---

{{ define "main" }}

<!-- Headline and Short Description -->
<h1 class="page-title">{{ .Title }}</h1>
<p>{{ .Params.description }}</p>

<!-- Workout Filter -->
<section class="workout-filter">
  <h2>Filter by Workout</h2>
  <div class="filter-buttons">
    <button data-filter="arms">Arms</button>
    <button data-filter="legs">Legs</button>
    <button data-filter="abs">Abs</button>
    <button data-filter="all">Show All</button>
  </div>
</section>

<!-- Exercise List Section -->
<section class="exercise-list">
  <table>
    <thead>
      <tr>
        <th>Workout</th>
        <th>Muscle Group</th>
        <th>Exercise Name</th>
        <th>Instructions</th>
        <th>Equipment</th>
      </tr>
    </thead>
    <tbody id="exercise-table">
      {{ range .Site.Data.workouts }}
      <tr data-workout="{{ .workout }}">
        <td>{{ .workout }}</td>
        <td>{{ .muscle_group }}</td>
        <td>{{ .name }}</td>
        <td>{{ .get_ready }}</td>
        <td>{{ .set_go }}</td>
        <td>{{ .hot_tip }}</td>
        <td>{{ .equipment }}</td>
      </tr>
      {{ end }}
    </tbody>
  </table>
</section>

<script>
  document.querySelectorAll('.filter-buttons button').forEach(button => {
    button.addEventListener('click', function() {
      const filter = this.getAttribute('data-filter');
      const rows = document.querySelectorAll('#exercise-table tr');
      
      rows.forEach(row => {
        if (filter === 'all' || row.getAttribute('data-workout') === filter) {
          row.style.display = '';
        } else {
          row.style.display = 'none';
        }
      });
    });
  });
</script>



{{ end }}

