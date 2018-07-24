# Prerequisite
I assume that the following block defines a 3-line arrow function:

    (): void => {   // Line 1
                    // Line 2
    }               // Line 3


# The Issue
I am demonstrating that max-func-body-length fails to count body length correctly.
For instance, when you run `npm run lint` with this repository, lint says:

> [20, 5]: Max arrow function body length exceeded - max: 2, actual: 3

Actually, however, the function has 4 lines.

This happens because [it does not add 1 to `endLine - startLine` for calculation of body length](https://github.com/Microsoft/tslint-microsoft-contrib/blob/master/src/maxFuncBodyLengthRule.ts#L124).
