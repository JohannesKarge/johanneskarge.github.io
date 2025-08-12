---
layout: default
---

<section class="hero" id="about">
  <div class="container">
    <h1 class="hero-title">{{ site.data.profile.name }}</h1>
    <p class="hero-subtitle">{{ site.data.profile.title }}</p>
    <p class="hero-location"><i class="fas fa-map-marker-alt"></i> {{ site.data.profile.location }}</p>
    
    <div class="hero-links">
      <a href="mailto:{{ site.data.profile.email }}" class="btn btn-primary">
        <i class="fas fa-envelope"></i> Email
      </a>
      <a href="{{ site.data.profile.linkedin }}" target="_blank" class="btn btn-secondary">
        <i class="fab fa-linkedin"></i> LinkedIn
      </a>
      <a href="{{ site.data.profile.pse_profile }}" target="_blank" class="btn btn-secondary">
        <i class="fas fa-university"></i> PSE Profile
      </a>
    </div>
  </div>
</section>

<section class="about-section">
  <div class="container">
    <h2>About</h2>
    <p class="lead">{{ site.data.profile.summary }}</p>
    
    <h3>Research Interests</h3>
    <div class="research-interests">
      {% for interest in site.data.profile.research_interests %}
        <span class="tag">{{ interest }}</span>
      {% endfor %}
    </div>
  </div>
</section>

<section class="experience-section" id="experience">
  <div class="container">
    <h2>Experience</h2>
    <div class="timeline">
      {% for job in site.data.experience %}
      <div class="timeline-item">
        <div class="timeline-date">
          {{ job.start_date }} - {{ job.end_date }}
        </div>
        <div class="timeline-content">
          <h3>{{ job.title }}</h3>
          <h4>{{ job.company }}</h4>
          <p class="location"><i class="fas fa-map-marker-alt"></i> {{ job.location }}</p>
          <p>{{ job.description }}</p>
        </div>
      </div>
      {% endfor %}
    </div>
  </div>
</section>

<section class="education-section" id="education">
  <div class="container">
    <h2>Education</h2>
    <div class="timeline">
      {% for edu in site.data.education %}
      <div class="timeline-item">
        <div class="timeline-date">
          {{ edu.start_date }} - {{ edu.end_date }}
          {% if edu.duration %}
          <span class="duration">({{ edu.duration }})</span>
          {% endif %}
        </div>
        <div class="timeline-content">
          <h3>{{ edu.degree }}</h3>
          <h4>{{ edu.institution }}</h4>
          <p class="field">{{ edu.field }}</p>
          {% if edu.description %}
          <p class="description">{{ edu.description }}</p>
          {% endif %}
        </div>
      </div>
      {% endfor %}
    </div>
  </div>
</section>

<section class="projects-section" id="projects">
  <div class="container">
    <h2>Projects & Research</h2>
    <div class="timeline">
      {% for project in site.data.projects.projects %}
      <div class="timeline-item">
        <div class="timeline-date">
          {{ project.start_date }} - {{ project.end_date }}
          {% if project.duration %}
          <span class="duration">({{ project.duration }})</span>
          {% endif %}
        </div>
        <div class="timeline-content">
          <h3>{{ project.title }}</h3>
          {% if project.institution %}
          <h4>{{ project.institution }}</h4>
          {% endif %}
          {% if project.type %}
          <p class="project-type"><strong>Type:</strong> {{ project.type }}</p>
          {% endif %}
          {% if project.supervisor %}
          <p class="supervisor"><strong>Supervisor:</strong> {{ project.supervisor }}</p>
          {% endif %}
          <p class="description">{{ project.description }}</p>
          {% if project.skills %}
          <div class="project-skills">
            {% for skill in project.skills limit:5 %}
            <span class="skill-tag">{{ skill }}</span>
            {% endfor %}
          </div>
          {% endif %}
        </div>
      </div>
      {% endfor %}
    </div>
  </div>
</section>

<section class="skills-section" id="skills">
  <div class="container">
    <h2>Skills & Expertise</h2>
    
    <div class="skills-grid">
      <div class="skill-category">
        <h3>Core Competencies</h3>
        <div class="skill-tags">
          {% for skill in site.data.skills.top_skills %}
            <span class="skill-tag">{{ skill }}</span>
          {% endfor %}
        </div>
      </div>
      
      <div class="skill-category">
        <h3>Technical Skills</h3>
        <div class="skill-tags">
          {% for skill in site.data.skills.technical_skills %}
            <span class="skill-tag">{{ skill }}</span>
          {% endfor %}
        </div>
      </div>
    </div>
    
    <h3>Languages</h3>
    <div class="languages">
      {% for lang in site.data.skills.languages %}
      <div class="language-item">
        <span class="language-name">{{ lang.language }}</span>
        <span class="language-level">{{ lang.proficiency }}</span>
      </div>
      {% endfor %}
    </div>
    
  </div>
</section>

<section class="certifications-section" id="certifications">
  <div class="container">
    <h2>Licenses & Certifications</h2>
    <div class="certifications-grid">
      {% for cert in site.data.certifications.certifications %}
      <div class="certification-card">
        <div class="cert-header">
          <div class="cert-logo">
            <img src="{{ cert.logo | relative_url }}" alt="{{ cert.issuer }} logo" />
          </div>
          <div class="cert-issuer-badge" style="background-color: {{ cert.color }}20; color: {{ cert.color }}">
            {{ cert.issuer }}
          </div>
        </div>
        
        <div class="cert-body">
          <h3 class="cert-title">{{ cert.title }}</h3>
          
          <div class="cert-meta">
            <div class="cert-date">
              <i class="fas fa-calendar-check"></i>
              <span>{{ cert.date_issued }}</span>
            </div>
            
            {% if cert.credential_id %}
            <div class="cert-credential">
              <i class="fas fa-fingerprint"></i>
              <span>{{ cert.credential_id }}</span>
            </div>
            {% endif %}
          </div>
          
          {% if cert.skills and cert.skills.size > 0 %}
          <div class="cert-skills">
            {% for skill in cert.skills limit:4 %}
            <span class="cert-skill-tag">{{ skill }}</span>
            {% endfor %}
            {% if cert.skills.size > 4 %}
            <span class="cert-skill-more">+{{ cert.skills.size | minus: 4 }} more</span>
            {% endif %}
          </div>
          {% endif %}
          
          {% if cert.url %}
          <a href="{{ cert.url }}" target="_blank" class="cert-verify-btn">
            <i class="fas fa-external-link-alt"></i>
            Verify Credential
          </a>
          {% endif %}
        </div>
      </div>
      {% endfor %}
    </div>
  </div>
</section>

<section class="memberships-section" id="memberships">
  <div class="container">
    <h2>Memberships & Volunteering</h2>
    
    <h3>Professional Memberships</h3>
    <div class="timeline">
      {% for membership in site.data.memberships_volunteering.memberships %}
      <div class="timeline-item">
        <div class="timeline-date">
          {{ membership.start_date }} - {{ membership.end_date }}
          {% if membership.duration %}
          <span class="duration">({{ membership.duration }})</span>
          {% endif %}
        </div>
        <div class="timeline-content">
          <h4>{{ membership.organization }}</h4>
          <p class="role">{{ membership.role }}</p>
          {% if membership.description %}
          <p class="description">{{ membership.description }}</p>
          {% endif %}
        </div>
      </div>
      {% endfor %}
    </div>
    
    <h3>Volunteering</h3>
    <div class="timeline">
      {% for volunteer in site.data.memberships_volunteering.volunteering %}
      <div class="timeline-item">
        <div class="timeline-date">
          {{ volunteer.start_date }} - {{ volunteer.end_date }}
          {% if volunteer.duration %}
          <span class="duration">({{ volunteer.duration }})</span>
          {% endif %}
        </div>
        <div class="timeline-content">
          <h4>{{ volunteer.activity }}</h4>
          <p class="organization">{{ volunteer.organization }}</p>
          {% if volunteer.description %}
          <p class="description">{{ volunteer.description }}</p>
          {% endif %}
        </div>
      </div>
      {% endfor %}
    </div>
  </div>
</section>

<section class="contact-section" id="contact">
  <div class="container">
    <h2>Contact</h2>
    <p>Feel free to reach out for research collaborations or any other inquiries.</p>
    <div class="contact-info">
      <a href="mailto:{{ site.data.profile.email }}" class="contact-link">
        <i class="fas fa-envelope"></i> {{ site.data.profile.email }}
      </a>
      <a href="{{ site.data.profile.linkedin }}" target="_blank" class="contact-link">
        <i class="fab fa-linkedin"></i> LinkedIn Profile
      </a>
    </div>
  </div>
</section>
