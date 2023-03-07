# Style Guide and Spacing Calculations

## :fast_forward: TLDR
- **UI / UX team to drop use of the existing header spacing calculations.**
- Remove references to bootstrap variables pasted in to the xd file These are not used and this can be confusing as the values don't match the design.
- The style guide part of the design is very useful. This helps FE devs build out the design faster and more accurately.
- Consistency is really important for the FE Dev team :
  - consistent containers, typeface, font sizes, spacings, etc throughout pages of the design.
  - consistent use of the values laid out in the style guide throughout pages of the design / not deviating from those.
- UI / UX designers should generally be able to make decisions about font sizes and type scales, spacings and scales, etc that work for the design rather than needing to be constrained by the pre-existing values in the BS variables file. as these can be updated.

## :green_circle: Context :
Issue raised by ui/ux with using header spacing calculation (for title line-height and margins).

- Difficult to implement the calculation in the context of designs - e.g. implementing a margin bottom of 1*5 header font-size.
- Training not given to both designers, leading to different working methods.
- Need for clarity on whether to use the calculation for header line heights and margins or not going forward.

### Agreed action :
Alex to discuss with rest of FE devs on builds before we make a decision on its use.

## :green_circle: Summary of Convos with FE Dev Members :
- Unclear as to what the calculation relates to in codebase - differs from the default values for headers spacing etc in BS variables.
- The calculation is not used by majority of build devs or not considered critical.
- It has been problematic to implement on builds.
- Overall feeling that the style guide is very useful and helps make build process faster.
- Having explicit and consistent values e.g for font sizes, spacings, and container sizes, across pages on the design is important factor to building out the design. This can cause problems more so than the use / non-use of the header spacing calculation.
- Not everyone always clear when / how to best leverage the Bootstrap variables instead of overriding them.

## :green_circle: Outcome Notes
- See TLDR :)

## :green_circle: Images for Reference

Images of the header spacing calculation ref'd above :

![image (4)](https://user-images.githubusercontent.com/42029575/223164327-0a4bd36a-4e15-4c33-8992-45de22cbcbf2.png)

