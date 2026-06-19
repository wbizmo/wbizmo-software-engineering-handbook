# Lesson 05 Cheatsheet: Flexbox, Grid and Responsive Design

Flexbox:

    display: flex;

Direction:

    flex-direction: row;
    flex-direction: column;

Main axis alignment:

    justify-content: center;

Cross axis alignment:

    align-items: center;

Gap:

    gap: 20px;

Grid:

    display: grid;

Columns:

    grid-template-columns: repeat(3, 1fr);

Responsive media query:

    @media (max-width: 768px) {
      .grid {
        grid-template-columns: 1fr;
      }
    }

Mobile-first media query:

    @media (min-width: 768px) {
      .grid {
        grid-template-columns: repeat(3, 1fr);
      }
    }

Flexbox:
    One-dimensional.

Grid:
    Two-dimensional.

Key takeaway:
    Modern CSS layout depends heavily on Flexbox, Grid, and media queries.
