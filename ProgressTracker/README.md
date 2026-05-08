# Planory — Full-Stack Personal Productivity Web App

## Overview

Planory is a mobile-first personal productivity PWA that consolidates scheduling, habit tracking, and multi-view planning into a single platform. Built with Next.js, React, TypeScript, and Supabase, it supports real-time task, habit, and event management across 6 purpose-built views with each designed for a different way of looking at your week.

The app integrates directly with Google Calendar, handles DST-aware repeat event logic, and runs as an installable PWA with smooth swipe navigation and direction-aware view transitions. Everything from authentication to calendar sync to habit analytics is managed through a single centralized React Context, keeping state consistent across all views in real time.

## Views

- **Planner** — 7-column week grid with day-themed color coding, toggleable checkboxes, and swipe navigation on mobile
- **Calendar** — Full month grid with day detail panel, event and task completion counts per cell
- **Timeline** — Gantt-style horizontal timeline with zoom levels (24h, 12h, 6h, 3h), color-coded by item type, and a live "Now" line
- **Activity** — Tabbed view across Habits, Tasks, and Events showing active and completed items
- **Insights** — Habit completion analytics with progress bars, streak indicators, and day-of-week pattern charts
- **Pending** — Backlog manager for incomplete and carried-over tasks with move and reschedule actions

## How It Works

All data is stored in a 9-table PostgreSQL schema via Supabase, covering categories, habits, completions, events, tasks, todos, pending tasks, user preferences, and Google Calendar tokens. Google Calendar is integrated via OAuth by fetching and formatting events in real time with automatic token refresh, DST-aware timezone handling across 48+ IANA timezones, and repeat event generation within the current week range.

The entire app state such as data, computed values, overlays, form state, and user preferences is centralized in a single React Context with 50+ variables, keeping all 6 views in sync without prop drilling or redundant fetches.

## Key Features

- Google Calendar integration with secure OAuth flow, auto token refresh, and DST-aware repeat event logic
- Habit tracking with per-day completion, weekly percentage, streak indicators, and day-of-week pattern analytics
- Pending backlog system — move tasks to tomorrow, next Monday, or carry them over across weeks
- Mobile-first UI with swipe navigation, direction-aware view transitions, and a fixed bottom nav with FAB
- User preferences for timezone (48+ options), time format (12h/24h), and display name are applied everywhere
- Installable as a PWA with standalone display and maskable icons

## Accessing the Full Code

The complete source code, database schema, component library, and setup instructions are available in the private repository.

Feel free to reach out for access for interviews, collaboration, or evaluation purposes.

- **Email:** ksheerooo@gmail.com
- **LinkedIn:** [linkedin.com/in/ksheerajprakash](https://linkedin.com/in/ksheerajprakash)


🔗 GitHub Repository (private): [https://github.com/KsheerajP/progresstracker.git](https://github.com/KsheerajP/progresstracker.git)
