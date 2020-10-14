# Nurse Scheduling Problem solver

## Objective

### Problem

Given an **entity** that has X **employees** and needs to fill Y **roles** during Z **days** of the week, how can we get the most satisfiying solution, both for the entity and the employees.

### Constraints

#### Entity

- An entity in our example will be a bar and restaurant which should work from the morning until the night (for the sake of the example, we will say: 9AM : 2AM(+1)). But ultimately, this solution should be loose enough to adapt to more environments like hospitals or hostels, which revolves around human ressource management.

#### Days

- No assumption can be made on the number of working days in a week for a given entity
- Each day has static roles (ex: 1 bartender and 1 waiter) and dynamic ones, depending on the expected volume of customers.

#### Employee

- Each employee is able to work 1 to Y roles
- Each employee has availabilities constraints, sorted between hard constraints (day-offs, sick leaves), and soft constraints (preferences, late request for a shift change).
- Each employee is bound by administratives constraints: they cannot work more than 14 hours straight (_To be checked_), they need 7 hours of rest between each shift (_To be checked and completed_)
- Each employee has an amount of hours per week (or shift/week depending on businesses) that he/she need to assess in order to fulfill his contract. These hours can be slightly manipulated per week but the overall monthly amount should match the contract.

#### Roles

- Each role can be fulfilled by one employee or more, in exceptional cases. At the same time, one employee or more (in excpetional cases) can fulfill one role.

## Solution conception

The solver should be given a list of employees, of roles, working days and a list of constraints (the shape of which needs to be adapted to the processing of the solver).
It could output a 2D array of employees E(i,j), where i the day index and j the role index.

## Next steps

1. Add a skill balancing constraint: each employee has a mastery level of each role, and given a week, master bartenders should be spread out, like newcomers on roles
2. The solver should be able to propose, if hitting an unsolvable schema, people not trained for a role, but with close dependencies to it (thus we need a dependency tree involving all roles)
3. The solver should be able to add randomization in its solution, aka not always giving the same, best solution (each employee work the exact same hours each week).
4. The solver should be able to output potential inconsistencies in the current set of employees/availabilities
5. The solver should be able to take random added constraints (Julie cannot work on thursday now and Anna wants to work on Saturday night) and generate a new solution.
