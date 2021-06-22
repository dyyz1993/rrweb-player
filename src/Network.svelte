<script lang="ts">
import type { networkData } from "rrweb/typings/types";
import { beforeUpdate, onMount, tick } from "svelte";

  // export let data: Map<string,networkData>
  // export let a :any;
  export let arr :any[];

  $:map = arr.reduce((m,item)=>{ m.set(item.id,item); return m },new Map())

  // let c : Map<string,networkData>;
  // let len = 0 ;
  beforeUpdate(async ()=>{
    // arr.forEach(element => {
    //   map.set(element.id,element)
    // });
    // map = map;
    // console.log(data)
    // c = data;
    // await tick();
    // console.log(num2)
    
    // len = arr.length;
    // console.log([...c.entries()])
  })

  // $:map = 

  
  console.log(arr);
  
</script>


<style>

</style>

<div>
  {arr.length}
  <!-- {num2} -->
  <!-- {a} -->
  <!-- {len} -->
    <table>
        <thead>
          <td>method</td>
            <td>url</td>
            
            <td>status</td>
            <td>request headers</td>
            <td>response headers</td>
            <td>size</td>
            <td>time</td>
        </thead>
        <tbody>
          {#each [...map.entries()] as [id,item]}
          <tr>
            <td>{item.method}</td>
            <td>{item.url}</td>
            
            <td>{item.status}</td>
            <td>{Object.entries(item.reqHeaders).map(([k,v])=>`${k}:${v}`).join('\n')}</td>
            <td>{Object.entries(item.resHeaders).map(([k,v])=>`${k}:${v}`).join('\n')}</td>
            <td>{item.size}</td>
            <td>{item.displayTime}</td>
           
          </tr>
            
            
                     
            {/each}
        </tbody>
    </table>
</div>