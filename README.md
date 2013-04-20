# D3 Topological Sort

A demo with explanation and usage example can be found [here](http://davidstutz.github.com/d3-topological/).

## Usage

For details see the demo.

The data should be given as follows:

	[
		{
			"label": "choosing clothes",
			"dependencies": [8]
		}, {
			"label": "dress",
			"dependencies": [0, 7]
		}, {
			"label": "eat breakfast",
			"dependencies": [4, 5, 6]
		}, {
			"label": "leave",
			"dependencies": [1, 2]
		}, {
			"label": "make office",
			"dependencies": [8]
		}, {
			"label": "make toast",
			"dependencies": [8]
		}, {
			"label": "pour juice",
			"dependencies": [8]
		}, {
			"label": "shower",
			"dependencies": [8]
		}, {
			"label": "wake up",
			"dependencies": []
		}
	]
	
Include d3.topological.js and:

	d3.json('data.json', function(nodes) {
		// The data is given as shown above.
		// The algorithm adds a number property to each node.
		// The number represents the position of the node in the topological sort.
		var topological = d3.topological()
			.nodes(nodes)
			.sort();
			
		// The nodes can now be sorted using their number.
		d3.ascending(nodes, function(a, b){ return a.number - b.number; })
	});