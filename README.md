# Sweetwater Front-End Code Test

## Overview

This project is an implementation of the provided Figma product review prototype. My goal was to transform the design into reusable, data-driven components while maintaining a clean and maintainable codebase. I also focused on making sure the UI components were responsive to all screen sizes and accessible for all users.

## Tech Stack

### Vue
I chose Vue because it was one of the frameworks that was listed in the job description, but Vue also provides a focus on clean component architecture that makes it easy to create reusable UI elements.

### TypeScript

I chose TypeScript to improve maintainability and type safety throughout the application. Defining types for review data helps prevent errors and improves the experience for developers.

### Vite

I used Vite as the build tool because it provides fast startup times and a lightweight project structure that allows development to move quickly.

## Component Architecture

### Rating Summary
The Rating Summary component displays overall review information. This includes the average rating, total review count, and also how the ratings are distributed. This component is designed to present review insights before users browse individual reviews.

### Star Rating
The Star Rating component provides an interactive interface for selecting a product rating when submitting a review. By separating this functionality into its own component, it can be reused throughout the application wherever rating input is required.

### Rates
The Rates component is responsible for displaying the rating associated with a review. Separating display logic from input logic allows the application to reuse rating functionality while maintaining a clear separation of responsibilities.

### Review Form
The Review Form component allows users to create a review by providing a title, rating, review content, and optional images.

On desktop or larger screen layouts, I chose to keep the review form visible while users search existing reviews. My reasoning was that allowing users to reference other reviews while writing their own creates a more convenient and user-friendly experience.

### Review Gallery
The Review Gallery component displays customer reviews using data from the JSON file. The component renders review information and images, allowing the interface to scale as new review data is introduced.

## Data Driven Approach
The review content and images are rendered from the JSON data rather than being hardcoded into the application. This allows for maintainability and scalability while showing how the prototype can be transformed into reusable, data-driven components.

## Accessibility
I incorporated accessibility best practices into this code. The application incorporates semantic HTML elements, associated labels for form inputs, accessible button elements for interactive controls, and alt text for review images. These help improve usability for users who need to use screen readers or other accessibility tools.

## Responsiveness
Having a responsive design was very important throughout the development. The layout has been designed to adapt across desktop, tablet, and mobile screen sizes.

On smaller devices, the review form moves abovethe rating summary to create an easier reading and review experience while maintaining usability and readability across screen sizes.

## Running the Project
1. Clone the repository
2. Run ```npm install```
3. Run ```npm run dev```
