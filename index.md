---
layout: default
---

<section id="about" class="hero-section">
  <div class="container hero-grid">
    <div class="hero-copy">
      <p class="eyebrow">Macroeconomics · Financial Stability · Economic History</p>
      <h1>{{ site.data.profile.name }}</h1>
      <p class="role">{{ site.data.profile.title }}</p>
      <p class="lead">{{ site.data.profile.summary }}</p>
      <div class="hero-actions">
        <a class="button primary" href="{{ site.data.profile.cv | relative_url }}?v={{ site.data.profile.cv_version }}" target="_blank" rel="noopener">Download CV <span aria-hidden="true">↗</span></a>
        <a class="button secondary" href="mailto:{{ site.data.profile.email }}">Get in touch</a>
      </div>
    </div>
    <div class="hero-photo-wrap">
      <img class="hero-photo" src="{{ '/assets/profile-photo.jpg' | relative_url }}" alt="Portrait of {{ site.data.profile.name }}">
    </div>
  </div>
</section>

<section class="interests-section">
  <div class="container">
    <p class="section-kicker">Research interests</p>
    <div class="tag-list" aria-label="Research interests">
      {% for interest in site.data.profile.research_interests %}
        <span class="tag">{{ interest }}</span>
      {% endfor %}
    </div>
  </div>
</section>

<section id="research" class="research-section">
  <div class="container">
    <p class="section-kicker">Research</p>
    <h2>Current projects</h2>
    <p class="research-intro">{{ site.data.projects.intro }}</p>

    <div class="project-list">
      {% for project in site.data.projects.projects %}
        <article class="project-card">
          <p class="project-status">{{ project.status }}</p>
          <h3>{{ project.title }}</h3>
          <p class="authors">{{ project.authors }}</p>
          <div class="abstract">{{ project.abstract | markdownify }}</div>
          <div class="tag-list project-tags">
            {% for tag in project.tags %}
              <span class="tag tag-muted">{{ tag }}</span>
            {% endfor %}
          </div>
        </article>
      {% endfor %}
    </div>
  </div>
</section>

<section id="contact" class="contact-section">
  <div class="container contact-grid">
    <div>
      <p class="section-kicker">Contact</p>
      <h2>Research correspondence</h2>
      <p>For research-related enquiries, comments, or data discussions, please get in touch by email.</p>
    </div>
    <div class="contact-links">
      <a href="mailto:{{ site.data.profile.email }}">{{ site.data.profile.email }}</a>
      <a href="{{ site.data.profile.pse_profile }}" target="_blank" rel="noopener">Paris School of Economics profile <span aria-hidden="true">↗</span></a>
      <a href="{{ site.data.profile.ideas_repec }}" target="_blank" rel="noopener">IDEAS / RePEc profile <span aria-hidden="true">↗</span></a>
      <a href="{{ site.data.profile.linkedin }}" target="_blank" rel="noopener">LinkedIn <span aria-hidden="true">↗</span></a>
      <a href="{{ site.data.profile.cv | relative_url }}?v={{ site.data.profile.cv_version }}" target="_blank" rel="noopener">Curriculum vitae (PDF) <span aria-hidden="true">↗</span></a>
    </div>
  </div>
</section>
