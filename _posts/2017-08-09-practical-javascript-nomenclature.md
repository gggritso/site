---
title: Practical JavaScript Nomenclature
permalink: practical-javascript-nomenclature
subtitle: Universal Nomenclature Standards for Variables and Functions
---

This is a set of rules I set for our internal JavaScript style guide after finding nothing similar online. Having consulted a few of my colleagues and used these extensively myself, I stand by these guidelines and use them every day. I hope you find these either helpful or at least controversial. These rules are optimized for clarity and readability above all. They favour the code reviewer or code maintainer over the code author. Eventually, we are all the maintainer.

## Be Clear
- choose full words over contractions. `options` over `opts`,  `value` over `val`, `userDetailParameters` over `userDetParams`
- single-letter or otherwise cryptic variable names like `o`, `i`, `u1` are strictly not allowed, even loop counters. The only exception is for mathematical formulas where such variables (like `x`, `d1`, etc.) have specific meaning
- avoid vague verbs like `get`, `set`, `update`. A function name should indicate  _the level of the system_ where it operates. For example, `fetchUser` has a stronger indication that it’s getting the user from the API rather than from memory. `getUserFromAPI` or `api.getUser` are similarly unambiguous. Generally, words like `get` and `set` imply action on classes and variables, `fetch` and `update` imply the API, while `read` and `write` imply the filesystem
- avoid single-verb functions unless they are also ambiguous. A `reload` function in a controller is ambiguous, something more specific like `reloadUserData` or `reloadControllerData` is clearer

## Use Good Grammar
- use plural and singular forms correctly. Array variables should always have plural names (e.g. `users`, `promises` but never `var user = []`). This means avoiding vague names like `collection` and `list`, and specifying exactly what the list is of (e.g. `$elements`, `links`)
- use auxiliary verbs to describe boolean values or functions that return boolean values. Choose names like `canShowElement` and `shouldReturnHome` over `showElement` and `returnHome` or `showingElement`
- use primary verbs for functions and methods. Choose names like `goToNextPage()` and `fetchUser()` over `nextPage()` and `user()`
- use prepositions in functions that operate on multiple objects. Choose names like `setOrderAddressOfUser` (or `setAddressOfUserOrder` as appropriate) over `setUserOrderAddress`
- avoid homonyms if possible. For example, `opening` could be the progressive tense of the verb “open” or it could be a noun meaning a gap or hole, or it could be an adjective describing something that happens at the beginning of something. Make exceptions for this if the previous rule applies

## Be Specific
- a function’s name should completely describe everything it does including side-effects. This is accomplished either with general function names (e.g. `processUser`) or _very_ specific names (e.g. `updateUserAddressAndPaymentInformation`)
- if a function exists as a small subset or a small superset of another function, its name should reflect that. If a function called `callAPI` exists, an authentication-less analogue should be called `callAPIWithoutAuthentication`
- a variable should be given a specific name as soon as it gets a specific meaning. For example, the result of `Users.getFavouriteUser()` should be called `favouriteUser` over `user`

## Be Consistent
- if a function’s name lists its arguments (e.g. `changePaymentProfileForUser`) it should take the listed arguments in the listed order. `changePaymentProfileForUser` should take the arguments `paymentProfile` and `user`
- do not rename external concepts. If the system or the organization already refer to a certain concept by a specific name, resist renaming that concept in code

## Examples

### Ambiguous Booleans
A variable called `clearSearch` is ambiguous. It could specify whether a search is clear, or it could specify whether a search _should_ be cleared, etc. Using an auxiliary verb makes them clear. Choose names like `isSearchClear` and `shouldClearSearch`, for example.

### Specific Meaning
Variables that have a specific meaning should be called with their assigned meaning as soon as possible, and they should lose meaning when appropriate. Consider this example:

```
var coordinates = POSITIONING.getUserCoordinates();
return checkCoordinates( coordinates );

function checkCoordinates( userCoordinates ) {
  return userCoordinates.areWithin( CITIES.Toronto );
}
```

The names of the variables do not reflect their specific meanings. The method `getUserCoordinates` returns `userCoordinates` by definition. The function `checkCoordinates` checks a `coordinates` variable, by definition. Inside that function, coordinates don’t have any meaning aside from just being coordinates. Also, the verb `check` is too vague for this case. A better version:

```
var userCoordinates = POSITIONING.getUserCoordinates();
return areCoordinatesWithinToronto( userCoordinates );

function areCoordinatesWithinToronto( coordinates ) {
  return coordinates.areWithin( CITIES.Toronto );
}
```

### Signatures and Arguments
Here’s an example from an API wrapper:

```
function getProductByID( parameters ) {
  return $http.get( '/product', parameters );
}
```

This is a good example of function signatures not matching their parameters. A function called `getProductByID` strongly implies that it accepts an `id` parameter, which it should:

```
function getProductByID( id ) {
  return $http.get( '/product', { productID: id });
}
```

### Long Names and Ambiguity
These guidelines heavily favour long variable and function names, but there’s a pretty natural limit. Function names that have more than 5 major parts of speech (nouns, verbs, and adjectives) are candidates to be renamed. Names like `createMembershipPermissionGetter` (4 major parts of speech) or `checkIfRecipesAreLiked` (4 major parts of speech) are still fine, but anything longer needs to be renamed, especially if it’s the part of a public API for a component.

Renaming long functions requires some creativity to find a good name for the overall operation. Oftentimes, it’s also a sign that some refactoring is in order, to group common operations together. For example, consider this structure:

```
<div
  class="range"
  ng-repeat="range in $ctrl.ranges"
  ng-if="$ctrl.checkIfTimeSlotIsEnabledIsAvailableAndIsWithinRange( range )"
>
  { range.start } — { range.end }
</div>
```

```
function checkIfTimeSlotIsEnabledIsAvailableAndIsWithinRange( range ) {

  if ( range.status === 'unavailable' ) return false;
  if ( !range.enabled ) return false;

  var
    now = moment();

  if ( now.isBefore( range.start ) ) return false;
  if ( now.isAfter( range.end ) ) return false;
}
```

This name is too verbose (5 major parts of speech, by a conservative count). The best way to figure out a new name is to figure out how the result of the function is used, rather than what it does. Since this function is used to determine whether a range should be shown, `shouldRangeBeShown` is a good candidate for its name.
