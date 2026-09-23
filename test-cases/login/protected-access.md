# Unauthenticated Access to Protected Page — Test Cases
Feature: login
Scope: UI
Total: 1 case (Critical: 1, High: 0, Medium: 0, Low: 0)

---
ID: TC-LOGIN-PROTECTED-001
Title: Unauthenticated direct access to https://the-internet.herokuapp.com/secure redirects to login
Type: UI
Feature: login
Flow: protected-access
Priority: Critical
Tags: security, regression
Preconditions: No active session (no login cookie set / fresh browser context)
Test Data: None
Steps:
  1. Without logging in, navigate directly to https://the-internet.herokuapp.com/secure via the URL bar
Expected Result: User is redirected to https://the-internet.herokuapp.com/login and a flash message "You must login to view the secure area!" is displayed. The secure area content is never shown.
Linked Requirement: None
