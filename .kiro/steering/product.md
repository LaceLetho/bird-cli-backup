# Product Overview

bird is a fast CLI tool for interacting with X/Twitter via their undocumented GraphQL API using cookie-based authentication.

## Core Functionality

- Read tweets, threads, replies, and timelines
- Post tweets and replies (with media support)
- Manage bookmarks, likes, and follows
- Search tweets and users
- Fetch news and trending topics from X's Explore tabs
- List management and timeline viewing

## Key Characteristics

- Uses X/Twitter's internal GraphQL API (undocumented, subject to breaking changes)
- Cookie-based authentication (no password prompts, uses existing browser sessions)
- Supports Safari, Chrome, Firefox cookie extraction
- Can be used as both a CLI tool and a library
- Designed for reading primarily (writing operations may trigger bot detection)

## Important Constraints

- GraphQL query IDs rotate frequently and require periodic updates
- Rate limiting (429 errors) is common
- Bot detection is aggressive for write operations
- API can change without notice
