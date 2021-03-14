```
public class BFSGraph {

	int v;
	LinkedList adj[];

	public BFSGraph(int v) {
		this.v = v;
		this.adj = new LinkedList[v];
		for(int i=0; i<v; i++) {
			adj[i] = new LinkedList<Integer>();
		}
	}
	
	private void addEdge(int i, int j) {
		adj[i].add(j);
	}
	
	public static void main(String[] args) {
		BFSGraph graph = new BFSGraph(4);
		graph.addEdge(0,1);
		graph.addEdge(0,2);
		graph.addEdge(1,2);
		graph.addEdge(2,0);
		graph.addEdge(2,3);
		graph.addEdge(3,3);
		
		graph.BFS(2);
	}

	private void BFS(int s) {
		boolean[] visited = new boolean[v];
		
		visited[s] = true;
		LinkedList<Integer> queue = new LinkedList<>();
		queue.add(s);
		
		while(!queue.isEmpty()) {
			int node = queue.poll();
			System.out.println(node);
			
			Iterator<Integer> iterator = adj[node].listIterator();
		
			while(iterator.hasNext()) {
				int e = iterator.next();
				
				while(!visited[e]) {
					visited[e] = true;
					queue.add(e);
				}				
			}
		}
	}
}

```
