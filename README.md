# Test to show corrupt image

## Description
[IncludeOS: Issue #348](https://github.com/hioa-cs/IncludeOS/issues/348)

## Test
Adding instruction `__asm__("testl %eax, %ebx;");` to increase the size of the service by 4 byte. Find out where it fails and where it doesn't.

## Data
[tests.xlsx](tests.xlsx)


## Conclusion
When an image is on the last 1024 bytes of a track, the image won't start.

```
First track:
|-----------------------------xx| last two sectors indicated by 'x'.
Second track:
|-----------------------------xx|
```

Adding 4 byte to start a new track will make a runnable image.