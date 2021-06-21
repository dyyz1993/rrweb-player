<script lang="ts">
import type { networkData } from "rrweb/typings/types";
import { beforeUpdate, onMount } from "svelte";

  export let data: Map<string,networkData>
  export let a :any;


  let c : Map<string,networkData>;
  beforeUpdate(()=>{
    c = data;
    console.log([...c.entries()])
  })
  
</script>


<style>

</style>

<div>
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
          {#each [...c.entries()] as [id,item]}
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