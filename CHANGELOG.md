# 0.44.0

-   forked from original repository, it now works in foundry `v13` though things are a little offset
-   i don't feel like fixing the styling so things aren't offset and janky. it works

# 0.43.0

-   expose new `check.getFlatCheckDc` function to the API

# 0.42.1

-   fix issue when a fake actor is passed in a check roll

# 0.42.0

-   now cache conditionals DOM elements for a small boost in performance
-   fix conditionals icons showing on the left side of the viewport on hex grid scene

# 0.41.0

-   fixed and re-enabled conditional token display

# 0.40.2

-   re-enable conditional token display

# 0.40.1

-   fixed emanation templates freezing foundry

# 0.40.0

-   this is a system `6.0.1` and foundry `v12` release
-   fixed most of the broken features
-   added Polish localization (thanks to [Lioheart](https://github.com/Lioheart))
-   conditional token display was disabled until i find why/what is happening
    -   this doesn't impact flat check rolls or off-guard automation
    -   the module will just not change the state of visibility of tokens based their conditional status related to the currently selected token

# 0.39.1

-   fixed `off-guard` not applying when the attacker is hidden from its target

# 0.39.0

-   added a third `30ft. burst` template to the `seek` action
-   fixed template highlightGrid breaking cone templates
-   fixed custom template creation not working

# 0.38.0

-   this is a `5.14.0` release
-   due to a breaking change in the system, the core feature of the module had to be moved into another part of the roll chain
-   while testings have shown to be satisfying, it is hard to foresee all the ramifications that this change involves

# 0.37.1

-   added compatibility with the `Disable Game Canvas` setting

# 0.37.0

-   added a new `Conditional Icons Size` client setting which offers the possibility to change the size in pixel for the conditional icons shown on mouse over

# 0.36.0

-   you can now register your own wall creature calculation function (it needs to be registered after the foundry `init` hook)

```js
game.modules.get("pf2e-perception").custom.getCreatureCover = (
    originToken,
    targetToken,
    { perception: PerceptionRules, debug = false }
) => "none" | "lesser" | "standard" | "greater" | "greater-prone";
```

# 0.35.1

-   fixed hazard rolling visibility flat-checks

# 0.35.0

-   improved secret action messages for players
-   change the behavior of the `Seek` action when no token is targeted manually, it will no longer automatically select all available enemies and roll for them, leaving everything in the hands of the GM
-   added support for the `Create a Diversion` action
-   added a new `Use Seek Templates` client setting: when disabled, the `Seek` action will no longer bring up the templates dialog

# 0.34.2

-   fixed missing weapon runes strike adjustments

# 0.34.1

-   removed custom NPC vision (it is in the system now)
-   fixed `Greater Darkvision` check
-   fixed `See Invisibility` check

# 0.34.0

-   this is a `5.12.0` release
-   updated NPCs senses not being a simple string anymore
-   fixed template creation error

# 0.33.1

-   fixed the `set` rule element selector

# 0.33.0

-   this is a `5.10.3` release
-   fix templates not colliding with walls

# 0.32.0

-   this is a `5.9.2` release
-   maybe fixed stuff ?

# 0.31.0

-   this is a `5.9.1` release
-   fixed not being able to strike after the latest system update

# 0.30.0

-   some minor tweaks that shouldn't impact anything on the user end
-   added a fully detailed list of the api functions that have been exposed in the global to the wiki

# 0.29.1

-   fixed some styling

# 0.29.0

-   newly created hidden tokens (holding `alt` before dropping them onto the scene) will now automatically be `unnoticed` from targeted tokens
-   migrated all chat messages styles to a style sheet instead of having them inlined
-   now moves the `unhide` button to the left if the message has the `Critical & Fumble` buttons shown

# 0.28.3

-   updated system ephemerals extraction to be in sync with recent changes
-   fixed issue with manually added lesser cover never being accounted for

# 0.28.2

-   fixed another issue with actorless

# 0.28.1

-   fixed actorless error

# 0.28.0

-   updated for system version `5.6.0`

# 0.27.0

-   added `Noxious Vapors` to the list of mist templates
-   added `Dead Give Cover` setting (enabled by default)
-   added `Prone Give Cover` setting (enabled by default)
-   fixed system visibility conditions not being handled

# 0.26.0

-   added support for `Blinded` and `Dazzled` conditions

# 0.25.1

-   added `token.openHUD` to the API allowing the use of macros to open the perception HUD

# 0.25.0

-   added `ignored` cover RE selector, it is used to ignore a specific token as cover when the attacking token is its ally, enemy or both
    -   it works differently than all the other REs because it is neither applied to the attacker nor the target but instead to potentially covering tokens ; because of that, predicates to the RE are way less powerful
    -   this is useful for things like the `Aim-Aiding Rune`:
    ```json
    { "key": "PF2ePerception", "type": "cover", "selector": "ignored", "targets": "allies" }
    ```

# 0.24.0

-   added support for signed `dc` RE value (note that only one dc value will still be taken into account though)

# 0.23.0

-   updated the `getRollContext` override and all its helpers to be in sync with latest system version

# 0.22.1

-   fixed issue with `Center to Spread` standard cover option

# 0.22.0

-   this is a system `5.4.0` release
-   fixed check roll dc issue

# 0.21.0

-   the `hasStandardCover` api function has been replaced with `getWallCover`
-   you can now register your own wall cover calculation function:

```js
game.modules.get("pf2e-perception").custom.getWallCover = (originToken, targetToken) =>
    "none" | "lesser" | "standard" | "greater" | "greater-prone";
```

# 0.20.2

-   the `Flat Check` setting now defaults to `Roll Flat-Check` instead of `Cancel the Attack on failure`
-   fixed token actors without senses error

# 0.20.1

-   fixed not being able to re-use confirmation menus in certain circumstances

# 0.20.0

-   light exposure calculation will now only use the center the the tokens, this will not only reduce the amount of computation but will also fix the issue with tokens partially overlapping with walls

# 0.19.1

-   the off-guard modifier generated by the module will now mention it is an off-guard effect on top of giving its origin

# 0.19.0

-   this is an attempts at making the module compatible with all the system's `5.3.0` changes

# 0.18.1

-   fixed attacks without event error

# 0.18.0

-   the module doesn't use `RollOption` anymore to modify cover & visibility, it now has its own custom `Rule Element` instead
-   you should now be able to use most of the predicates with the `Rule Element` to fine tune the conditions for it to apply
-   added `CloudKill` to the list of automated mist templates (it will have a slight green-ish color)
-   added support for the `See Invisibility` system sense
-   flat checks generated by blindroll attacks will now also be rolled blind
-   fixed token actors without sense but with token vision breaking the detection

# 0.17.0

-   complete rework of the detection, the module now respects the vision source (i.e. no more tokens undetected for all owned/observed tokens for players), the detection now also completely uses the conditionals and the rollOptions
-   added support for the `invisible` condition, it will automatically apply the `hidden` state to the token if the current one isn't at least that high
-   added `visibility:seeinvis:all` rollOption which will reduce the `hidden` or `undetected` state of a token to `concealed` if they are `invisible`
-   added `Stinking Cloud` to the list of automated mist templates
-   the `prone-cover` option is now always shown in the perception and validation menus
-   rollOption will now properly work when the attacker <-> target roles are reversed
-   fixed greater darkvision not working
-   fixed issue with the `reduce` rollOption when using the default values `none` and `observed`

# 0.16.0

-   added support for mist templates, it works the same way as darkness templates (exposed its functions to the API)
-   tokens selected (and highlighted) by the seek action templates will now use the position of the token that is seeking as collision origin instead of the template's origin itself, preventing tokens behind corners to be selected by the template
-   removed GM auto opening of validation menus
-   fixed darkvision removing non light/darkness related `hidden` (#12)

# 0.15.0

-   added support for darkness templates, some spells are automatically handled, the module will update the detection as well as use them to modify the visibility on attacks
-   added button to the seek action chat card to delete the associated template
-   exposed even more functions to the API including `createSeekTemplate` and `createDarknessTemplate`
-   the `seek` action now uses a `sight` template which means that walls that don't block sight will not block the seek template
-   fine tuned how the `seek` action works when no template is used
-   the warning message about `PF2e Rules-Based NPC Vision` will now indicate which module it refers to instead of the cryptic `this`

# 0.14.0

-   `darkvision` is no longer taken into account for conditional `hidden` in PoV detection
-   fixed flat-check degree of success not doing anything
-   fixed numerical rollOptions values not being cast as numbers

# 0.13.0

-   only account for `darkvision` and `low-light vision` for the visibility provided by the light exposure part of the module
-   removed `Automate Light Exposure` setting, this cannot be optional if we want `darkvision` and `low-light vision` to ever be taken into account
-   reverted not showing conditional icons when the actor had `low-light vision` and `darkvision`

# 0.12.0

-   `concealed` and `hidden` conditional icons will no longer show up if the hovered token actor has respectively `low-light vision` and `darkvision`
-   fixed error with messages that were generated without the module active of with a previous version of the module
-   fixed PoV vision showing tokens as hidden when selected token has darkvision

# 0.11.2

-   fixed flat-check not working with system version `5.2.3`
-   fixed automated creature cover testing against target token itself

# 0.11.1

-   fixed flat-footed being applied when hidden attacker was targeting a token with darkvision
-   fixed issue with extra large creature hidden in scene messing up with the automated creature cover test always returning standard cover

# 0.11.0

-   added NPC `Rule Based Vision` support, you need to enable the vision on the NPC tokens for it to take action
-   added `Force NPC Vision` setting which will force the `Vision Enabled` option on newly created NPC tokens, this can be set on a per-scene basis
-   added a warning if the `PF2e Rules-Based NPC Vision` module is active, both modules will conflict with each other
-   moved custom context flags into a single namespace
-   fixed issue with the rollOption `set` when using `none` and `observed`

# 0.10.0

-   added `cover|visibility:set:x` rollOption to force a cover|visibility state equal to `x`, here `x` cannot be `all` but accept `none` for cover and `observed` for visibitlity
-   added a button in attack chat cards which allows the GM to un-hide the token that initiated the attack
-   added support for NPC senses using the senses shown in `Special Senses` field ; also, and even though the system doesn't support it and gives a warning, NPCs can use the `Sense` Rule Element to add temporary vision senses (e.g. using a darkvision spell effect or similar)
-   messages are now parsed during the `ready` hook on first load and after a refresh of the browser tab
-   the module will no longer roll a flat-check for hidden targets when the attacker has darkvision
-   changed the rollOption `visibility:noflat:x` to be `visibility:noff:x`, the former could be confused with "no flat-check" instead of "no flat-footed" (i confused myself with it...)

# 0.9.0

-   did a complete refactor of the rollOptions, you can find a summary of how they work here: https://github.com/reonZ/pf2e-perception#roll-options

# 0.8.0

-   added support for custom rollOptions, those can be added via the system `RollOption` or directly provided in the attack options arguments, here is an example on how to implement the `Blind-Fight` feat, just add those 3 REs in the feat itself:
-   removed automated support for the `Blind-Fight` feat
-   you can now manually override a cover in the modifiers window (the one you need to hold shift to show or not show during a check roll)

# 0.7.2

-   fixed an issue brought by `11.306`

# 0.7.1

-   fixed issue with automated light exposure always considering tokens `hidden` in scenes that had vision/exposure disabled or not in the dark

# 0.7.0

-   replaced `Automate Concealment` setting with `Automate Light Exposure`
-   the system now check if a token is in bright light, dim light or darkness when it comes to automatically checking its visibility state
-   added `Perception Menu Permission` setting which allow you to select which minimum permission a user must have to be able to interact with the perception menu (keep in mind that the menu is a major spoiler if given access to players)
-   added `Conditional Icons` settings menu where you can set custom path to icon images that will be displayed on token hover
-   added `Flat Check` setting allowing you to disabled module flat checks, roll flat checks before attacks or canceling the attacks entirely on failure
-   the `Hide` and `Seek` actions now properly use the degree of success provided by natural 20/1
-   you can now also validate the `Seek` action even without having used a template (you can also manually target)
-   automated creature cover will no longer care for the type of attack (reach, ranged, etc.), it will still require a minimum of 1 square of distance between attacker and target
-   when a player hover over a token, they will not be shown visibility tokens above `concealed` if the other token isn't owned by a player, this prevent players from knowing if they are indeed hidden/undetected from another token
-   fixed validation buttons not showing up on chat message roll cards when using `Dorako UI` module
-   fixed issue with orphan tokens
-   fixed target-less point-out error
-   fixed greater cover giving the wrong bonus value

# 0.6.1

-   fixed a bug during automated concealment check preventing attacks

# 0.6.0

-   non-listed first release
