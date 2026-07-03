# Deploying this update

1. Unzip this package.
2. Replace the contents of your GitHub repository `JohannesKarge/johanneskarge.github.io` with the extracted source files.
3. Commit and push to the `main` branch.
4. GitHub Pages will rebuild automatically. The live site normally updates within a few minutes.

The new CV is already included at `assets/cv.pdf`. Every CV link contains a version parameter to avoid browser caching. On a later CV update, replace that file and update `cv_version` in `_data/profile.yml`.

The homepage no longer reads or renders the former experience, education, skills, certifications, or memberships data files.
