# Stop Writing React Native Styles Like It's 2022

Original clipping: [YouTube](https://www.youtube.com/watch?v=J8hmOaA5uzc)  
Author: Code with Beto  
Published: 2026-04-09  
Processed: 2026-05-10

## Summary

The clipping argues that modern React Native supports several web-aligned style props that reduce the need for third-party UI libraries: `backgroundImage` for gradients, `filter`, `boxShadow`, `gap` / `rowGap` / `columnGap`, and `mixBlendMode`.

## Verified Updates

- React Native 0.76 introduced New Architecture-only `boxShadow` and `filter` style props.
- Current React Native style docs list `boxShadow` and `mixBlendMode`, with important platform and OS limits.
- Current React Native flexbox docs list `gap`, `rowGap`, and `columnGap`.
- `filter` remains limited on iOS: current React Native release notes document iOS support for brightness and opacity only, with broader support on Android.
- `mixBlendMode` is New Architecture-only and Android 10+ according to current React Native style docs.

## Web Sources Checked

- [React Native 0.76 release notes](https://reactnative.dev/blog/2024/10/23/release-0.76-new-architecture)
- [React Native View Style Props](https://reactnative.dev/docs/view-style-props)
- [React Native Flexbox: gap, rowGap, columnGap](https://reactnative.dev/docs/flexbox)

## Related Pages

- [[Mobile Development/React Native/Styling/Modern React Native Style Props]]
