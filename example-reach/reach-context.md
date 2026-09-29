# Reach: product context

## What Reach is
Reach puts Instagram and YouTube numbers in one place: a dashboard of daily figures, plus draft captions and descriptions to copy out by hand. It is read-only by design. Nothing is ever posted to either platform from Reach.

## What exists today
- A design preview, live at social-media-engagement-website.vercel.app. Every figure on it is sample data, and nothing is connected to Instagram or YouTube yet.
- Three pages:
  - **Home.**
  - **Dashboard:** followers, reach, subscribers and watch time; a 14-day chart of daily interactions; the Instagram and YouTube split with an engagement rate; and a table of recent posts.
  - **Drafts:** caption and description drafts, with tone and platform switches and copy to clipboard.
- Built with plain HTML, CSS and JavaScript and served as static files, with no backend, database or login.

## How Reach counts engagement today (dashboard)
- Interactions = likes + comments.
- Engagement rate = interactions ÷ reach, shown to one decimal (for example, 5.7%).

## Constraints for new features
- Anything a feature does with a user's file must happen in their browser. There is no server to send it to and nowhere to store it.
- Pages must work on a phone 360 px wide as well as on a laptop.
- Numbers are shown in Indian format (1,25,000) and dates as DD-MM-YYYY.
- Only Instagram and YouTube are supported.

## What's being tested now
- The CSV report card. Its requirements were baselined as v1 on 28-09-2026, in the BA's handoff file (stories with acceptance criteria, the field spec and the business rules).
- The feature isn't built yet. The test cases are written from the requirements now and run on the build later.
