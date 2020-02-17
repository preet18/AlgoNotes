```public class HashMap {

	private static final int SIZE = 4;
	
	private static Entry table[] = new Entry[SIZE];
	
	class Entry{
		 final String key;
		 String value;
		 Entry next;
		 
		 Entry(String k, String v){
			 key = k;
			 value = v;
		 }
		 
		 public String getValue(){
			 return value;
		 }
		 
		 public void setValue(String value){
			 this.value = value;
		 }
		 
		 public String getKey(){
			 return key;
		 }
		 
	}
	
	public Entry get(String k){
		int hash = k.hashCode()%SIZE;
		Entry e = table[hash];
		
		while(e!=null){
			if(e.key.equals(k)){
				return e;
			}
			e = e.next;
		}
		return null;
	}
	
	public void put(String k, String v){
		int hash = Math.abs(k.hashCode())%SIZE;
		//System.out.println("Hash :: " + hash);
		Entry e = table[hash];
		boolean inserted = false;
		if(e!=null){
			
			if(e.key.equals(k)){
				System.out.println("Key already exists in the bucket....");
				e.value = v;
			}else{
				while(e.next!=null){
					e = e.next;
					if(e.key.equals(k)){
						System.out.println("Key already exists in the bucket....");
						e.value = v;
						inserted = true;
						break;
					}
				}
				if(!inserted){
					Entry entryInOldBucket = new Entry(k, v);
					e.next = entryInOldBucket;
				}
			}
			
		}else{
			Entry entryInNewBucket = new Entry(k, v);
			table[hash] = entryInNewBucket;
		}
	}
	
	
	public static void main(String[] args){
		HashMap hm = new HashMap();
		
		hm.put("Awadh", "SSE");
		hm.put("Rahul", "SSE");
		hm.put("Sattu", "SE");
		hm.put("Gaurav", "SSE");
		hm.put("Preeti", "SE");
		hm.put("Sattu", "SSE");
		/*hm.put("Nayudu", "SSE");
		hm.put("Mahathi", "SE");
		hm.put("Naga", "SE");*/
		
		Entry e = hm.get("Awadh");
		System.out.println(e.getValue());
		
		//int count = 0;
		for(int i=0; i<SIZE; i++){
			System.out.println("Index :: " + i);
			Entry entry = table[i];
			while(entry!=null){
				System.out.println(entry.getKey() + " - " + entry.getValue());
				entry = entry.next;
				
			}
		}
	}
	
}```
