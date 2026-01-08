# Bug Investigation Checklist

## Quick Checks
- [ ] Is the environment correctly configured (env vars, dependencies)?
- [ ] Are there any obvious errors in the console/logs?
- [ ] Has the code been recently updated?
- [ ] Does the issue persist after clearing caches or re-building?

## Logic & Data
- [ ] Are all inputs validated?
- [ ] Are there any hidden null/undefined values?
- [ ] Is there an off-by-one error in a loop or slice?
- [ ] Are asynchronous operations correctly awaited?

## Performance & State
- [ ] Is there a memory leak (unclosed resources, growing collections)?
- [ ] Is there a race condition in concurrent code?
- [ ] Is the state being mutated unexpectedly?

## Technology Specifics
### React/Frontend
- [ ] Are hooks used correctly (deps arrays)?
- [ ] Is there a re-render loop?
- [ ] Is the issue specific to a certain browser or screen size?

### Backend/API
- [ ] Are database transactions correctly handled?
- [ ] Is there an N+1 query problem?
- [ ] Are error responses descriptive enough?
