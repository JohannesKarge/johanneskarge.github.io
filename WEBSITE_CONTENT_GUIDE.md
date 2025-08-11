# Website Content Guide

This guide explains how to update and modify the content of Johannes Karge's portfolio website.

## Table of Contents
1. [Website Overview](#website-overview)
2. [Quick Start](#quick-start)
3. [Updating Personal Information](#updating-personal-information)
4. [Modifying Content Sections](#modifying-content-sections)
5. [Adding New Content](#adding-new-content)
6. [Testing Changes Locally](#testing-changes-locally)
7. [Deploying to GitHub Pages](#deploying-to-github-pages)

## Website Overview

This is a Jekyll-based static website that uses YAML data files to manage content. The site automatically builds and deploys to GitHub Pages when you push changes to the repository.

### Key Technologies
- **Jekyll**: Static site generator that converts Markdown and data files into HTML
- **YAML**: Human-readable data format used for content storage
- **Liquid**: Templating language used in Jekyll for dynamic content
- **GitHub Pages**: Free hosting service that automatically builds Jekyll sites

### Directory Structure
```
johanneskarge.github.io/
├── _data/                  # Content data files (YAML)
│   ├── profile.yml        # Personal information
│   ├── experience.yml     # Work experience
│   ├── education.yml      # Educational background
│   ├── projects.yml       # Research projects
│   ├── skills.yml         # Technical skills
│   ├── certifications.yml # Professional certifications
│   └── memberships_volunteering.yml
├── _layouts/              # Page templates
│   └── default.html       # Main layout template
├── assets/                # Static assets
│   ├── css/              # Stylesheets
│   └── images/           # Images and logos
├── _config.yml           # Site configuration
└── index.md              # Homepage content
```

## Quick Start

To make changes to the website content, you only need to edit the YAML files in the `_data/` directory. No HTML or programming knowledge is required for content updates.

## Updating Personal Information

### Basic Profile (_data/profile.yml)

Edit `_data/profile.yml` to update:
- Name and title
- Location
- Email address
- LinkedIn profile URL
- PSE profile URL
- Professional summary
- Research interests

**Example:**
```yaml
name: Johannes Karge
title: PhD Candidate at Paris School of Economics
location: Paris, Île-de-France, France
email: j.r.karge@gmail.com
linkedin: https://www.linkedin.com/in/johannes-karge
pse_profile: https://www.parisschoolofeconomics.eu/en/people/johannes-karge/

summary: |
  Your professional summary here. Use the pipe (|) symbol
  for multi-line text.

research_interests:
  - Macroeconomics
  - Financial Stability
  - Banking
```

### Site Configuration (_config.yml)

Update `_config.yml` for:
- Website title
- Meta description
- Author name
- Contact email
- Site URL (when deploying)

## Modifying Content Sections

### Work Experience (_data/experience.yml)

Add or modify work experience entries:

```yaml
- company: Company Name
  title: Your Job Title
  start_date: January 2024
  end_date: Present  # or specific date
  location: City, State/Region, Country
  description: |
    Description of your role and responsibilities.
    Can be multiple lines using the pipe symbol.
```

### Education (_data/education.yml)

Update educational background:

```yaml
- institution: University Name
  degree: Degree Type (e.g., PhD, Master's)
  field: Field of Study
  start_date: September 2020
  end_date: June 2024
  duration: 4 years  # Optional
  description: Additional details about your studies  # Optional
```

### Projects & Research (_data/projects.yml)

Add research projects:

```yaml
projects:
  - title: Project Title
    institution: Institution Name  # Optional
    type: Research Paper / Thesis / etc.
    supervisor: Supervisor Name  # Optional
    start_date: January 2023
    end_date: December 2023
    duration: 1 year  # Optional
    description: Project description
    skills:  # Optional list of technologies/methods used
      - Python
      - Econometrics
      - Data Analysis
```

### Skills (_data/skills.yml)

Update technical and language skills:

```yaml
top_skills:
  - Data Analysis
  - Economic Research
  - Statistical Modeling

technical_skills:
  - Python
  - R
  - Stata
  - MATLAB

languages:
  - language: English
    proficiency: Native/Fluent
  - language: French
    proficiency: Professional
  - language: German
    proficiency: Intermediate
```

### Certifications (_data/certifications.yml)

Add professional certifications:

```yaml
certifications:
  - title: Certification Name
    issuer: Issuing Organization
    date_issued: January 2024
    credential_id: ABC123  # Optional
    url: https://verify.certification.com/ABC123  # Optional
    logo: /assets/images/certifications/logo.svg
    color: "#0066CC"  # Brand color for styling
    skills:  # Optional
      - Related Skill 1
      - Related Skill 2
```

### Memberships & Volunteering (_data/memberships_volunteering.yml)

Update professional memberships and volunteer work:

```yaml
memberships:
  - organization: Organization Name
    role: Member / Board Member / etc.
    start_date: January 2023
    end_date: Present
    duration: 2 years  # Optional
    description: Description of involvement  # Optional

volunteering:
  - activity: Volunteer Activity
    organization: Organization Name
    start_date: June 2022
    end_date: August 2022
    duration: 3 months  # Optional
    description: Description of volunteer work  # Optional
```

## Adding New Content

### Adding Images

1. Place images in `assets/images/` directory
2. For certification logos: `assets/images/certifications/`
3. Reference in YAML files using relative paths:
   ```yaml
   logo: /assets/images/certifications/company-logo.svg
   ```

### Creating New Data Categories

1. Create a new YAML file in `_data/` directory
2. Add corresponding section in `index.md` using Liquid templating
3. Style the new section in `assets/css/style.scss`

**Example:** Adding a Publications section

1. Create `_data/publications.yml`:
```yaml
- title: Paper Title
  authors: J. Karge, Co-author
  journal: Journal Name
  year: 2024
  url: https://link-to-paper.com
```

2. Add to `index.md`:
```html
<section class="publications-section" id="publications">
  <div class="container">
    <h2>Publications</h2>
    {% for pub in site.data.publications %}
    <div class="publication-item">
      <h3>{{ pub.title }}</h3>
      <p>{{ pub.authors }} ({{ pub.year }})</p>
      <p><em>{{ pub.journal }}</em></p>
      {% if pub.url %}
      <a href="{{ pub.url }}">View Paper</a>
      {% endif %}
    </div>
    {% endfor %}
  </div>
</section>
```

## Testing Changes Locally

### Prerequisites
- Ruby (version 2.5 or higher)
- Bundler gem

### Setup and Running

1. **Install Jekyll and dependencies:**
   ```bash
   bundle install
   ```

2. **Run the local server:**
   ```bash
   bundle exec jekyll serve
   ```
   
3. **View your site:**
   Open browser and go to `http://localhost:4000`

4. **Making changes:**
   - Edit YAML files in `_data/`
   - Save changes
   - Browser will auto-refresh (if not, manually refresh)

### Troubleshooting Local Development

- **Port already in use:** Use `bundle exec jekyll serve --port 4001`
- **Changes not showing:** Clear browser cache or use incognito mode
- **Build errors:** Check YAML syntax (proper indentation is crucial)

## Deploying to GitHub Pages

### Automatic Deployment

The site automatically deploys when you push changes to the `main` branch:

1. **Make your changes locally**
2. **Commit changes:**
   ```bash
   git add .
   git commit -m "Update profile information"
   ```

3. **Push to GitHub:**
   ```bash
   git push origin main
   ```

4. **Wait for deployment:**
   - GitHub Actions will automatically build and deploy
   - Takes 2-5 minutes typically
   - Check Actions tab on GitHub for build status

### Manual Deployment Check

1. Go to repository Settings
2. Navigate to Pages section
3. Verify source is set to "Deploy from a branch"
4. Branch should be `main` and folder should be `/ (root)`

### Custom Domain (Optional)

To use a custom domain:

1. Add a `CNAME` file in the root directory with your domain:
   ```
   www.yourdomain.com
   ```

2. Configure DNS settings with your domain provider:
   - Add CNAME record pointing to `[username].github.io`
   - Or add A records to GitHub's IP addresses

3. Update `_config.yml`:
   ```yaml
   url: "https://www.yourdomain.com"
   ```

## Best Practices

### Content Guidelines

1. **YAML Formatting:**
   - Use consistent indentation (2 spaces recommended)
   - Quote strings containing special characters
   - Use pipe `|` for multi-line text

2. **Dates:**
   - Use consistent format (e.g., "January 2024" or "Jan 2024")
   - Use "Present" for current positions

3. **Descriptions:**
   - Keep concise and professional
   - Use bullet points for clarity (with `-` in YAML)
   - Highlight key achievements and skills

### Version Control

1. **Commit frequently** with descriptive messages
2. **Test locally** before pushing to main
3. **Keep backups** of important content changes
4. **Use branches** for major redesigns:
   ```bash
   git checkout -b new-feature
   # Make changes
   git push origin new-feature
   # Create pull request on GitHub
   ```

### Performance Tips

1. **Optimize images:**
   - Use SVG for logos when possible
   - Compress JPG/PNG files
   - Keep images under 500KB

2. **Limit content:**
   - Show only recent/relevant experience
   - Use pagination for long lists
   - Archive old content separately

## Common Issues and Solutions

### Content Not Updating

**Problem:** Changes to YAML files don't appear on the website

**Solutions:**
- Check YAML syntax (use online YAML validator)
- Ensure proper indentation
- Clear browser cache
- Check GitHub Actions for build errors

### Build Failures

**Problem:** GitHub Pages build fails

**Solutions:**
- Check `_config.yml` for syntax errors
- Verify all referenced files exist
- Check Gemfile.lock is not outdated
- Review error message in GitHub Actions tab

### Styling Issues

**Problem:** Content appears unstyled or broken

**Solutions:**
- Check CSS file path in `_layouts/default.html`
- Verify `assets/css/style.css` exists
- Clear browser cache
- Check browser console for errors

## Additional Resources

- [Jekyll Documentation](https://jekyllrb.com/docs/)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [YAML Syntax Guide](https://yaml.org/spec/1.2/spec.html)
- [Liquid Template Language](https://shopify.github.io/liquid/)
- [Markdown Guide](https://www.markdownguide.org/)

## Support

For issues specific to this website structure:
1. Check this guide first
2. Review GitHub Actions logs for build errors
3. Test changes locally before pushing
4. Create an issue in the repository if problems persist

---

*Last updated: January 2025*