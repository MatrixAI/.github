---
name: Blog Post
about: Template for drafting new blog post content for the Polykey Website
title: 'Blog Post - [Title Here]'
labels: blog
assignees: ''

---

## Introduction

This template guides contributors through the process of creating and submitting a blog post on the Polykey website. Please follow the steps meticulously to ensure consistency and quality in our blog content.

### Step 1: Create a New Markdown File

- **Location**: Navigate to the `blog` folder in the repository.
- **Action**: Create a new `.md` file.
- **Naming Convention**: Use the following format for naming your file: `YYYY-MM-DD-insert-title-of-blog.md`.
  - **Example**: `2024-04-15-exploring-zero-trust-security.md`

### Step 2: Insert Metadata

Insert the required metadata at the top of your Markdown file using the format below:

```yaml
---
slug: insert-title-of-blog
title: Insert Title of Blog Here
authors: first-name
tags: [keyword1, keyword2]
---
```

- **Slug**: This is the title without the date and should be the same as the title in the filename but with hyphens instead of spaces.
- **Title**: A readable version of the slug, which can include punctuation and does not contain hyphens.
- **Authors**: Your first name, or the handle that matches an entry in `authors.yml`.
- **Tags**: Include relevant topic tags for SEO purposes.
- **Note**: The content of your post will begin immediately under the closing `---`.

### Step 3: Author Details (If Necessary)

- If your details are not in `authors.yml`, add them in the following format:

```yaml
pablo:
  name: Pablo Padillo
  title: Software Engineer
  url: https://github.com/CryptoTotalWar
  image_url: https://avatars.githubusercontent.com/u/107008759?v=4
```

### Step 4: Include Images (If Any)

- **Image Storage**: Save any images used in your blog post within the images folder of the repository.
- **Referencing Images**: Make sure to reference these images using relative paths in your blog post.

### Step 5: Create a Pull Request

- Once your blog post is ready for review, create a new PR prefixed with `feature-` to share the draft found at `feature-x.dev.polykey.com` and receive feedback from the team.
  - **Example PR title**: `feature-blog-my-exciting-polykey-journey`
  - After pushing the PR, a web-hosted version can be viewed at `feature-blog-my-exciting-polykey-journey.dev.polykey.com`

## Blog Post Submission Checklist
Ensure that you have completed each of the following steps by checking them off as you go. Include detailed notes or responses for each section as necessary.

### Blog Content Verification
- [ ] **Introduction Checked**
  - **Notes/Responses:**
    - Describe any key themes or introductions highlighted in this section.

- [ ] **Main Content Points Reviewed**
  - [ ] **Subtopic One Covered**
    - **Notes/Responses:**
      - Detail insights or discussions included here.
  - [ ] **Subtopic Two Covered**
    - **Notes/Responses:**
      - Outline arguments or data points discussed.
  - [ ] **Subtopic Three Covered**
    - **Notes/Responses:**
      - Explain integration with overall blog theme.

### Additional Content Checks
- [ ] **Relevant Statistics/Data Utilized**
  - **Notes/Responses:**
    - Confirm statistics or data sources used and their validity.

- [ ] **Case Studies or Examples Used**
  - **Notes/Responses:**
    - Detail any case studies or real-world examples incorporated.

- [ ] **Conclusion and Call to Action Formulated**
  - **Notes/Responses:**
    - Summarize the conclusion and what actions readers should take.

### SEO and Compliance
- [ ] **SEO Keywords Implemented**
  - **Notes/Responses:**
    - List SEO keywords targeted in this post.

- [ ] **Compliance with Style Guidelines**
  - **Notes/Responses:**
    - Confirm adherence to style or tone guidelines.

### Images and Media
- [ ] **Images Properly Referenced**
  - **Notes/Responses:**
    - Verify that images are stored correctly and referenced.

### Final Review
- [ ] **PR Ready for Review**
  - **Notes/Responses:**
    - Any final notes or adjustments needed before final review.

### Additional Information
- **Related Documents or Previous Posts:**
  - Include links or references to related documents or previously published posts that are connected to this topic.
