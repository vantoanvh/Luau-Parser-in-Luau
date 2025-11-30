# Luau Parser in Luau
Entire port of [Parser.cpp](https://github.com/luau-lang/luau/blob/master/Ast/src/Parser.cpp) (Luau 0.701 Parser) both AST & CST.

# Public API

```luau
Parser.parse(source: string, options: Options): boolean, result
```

These had some plenty of options
```luau
{
	-- Turns off by default, Luau only enables this syntax feature when it knows it is parsing a Definition File
	allowDeclarationSyntax: boolean,
	-- Turns off by default, Defines parser will save comments or not
	captureComments: boolean,
	-- Turns off by default, Defines parser will store CST (result.cstNodeMap) or not
	storeCstData: boolean,
	-- Turns off by default, Remove luau parser error limit (100) or not
	noErrorLimit: boolean,
	-- Able to start on a different point of the source
	parseFragment: {
		resumePosition: Position?,
		localMap: {[string]: any},
		localStack: {any}
	}?
}
```

Also a result format
```luau
{
	-- Contains all AST nodes of the source
	root: {AstNode},

	-- Contains all the comments locations (if captureComments is enabled)
	commentLocations: {Comment},

	-- Contains all the "--!" comments
	hotcomments: {Comment},

	-- Contains all CST nodes of the source, which you can get it by indexing cstNodeMap[AstNode] = CstNode
	cstNodeMap: {CstNode},

	-- Contains all parsing errors
	errors: {ParseError},
}
```

There's no AST and CST documentation for now
