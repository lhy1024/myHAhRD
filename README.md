# Summary  
## Requirement  
In order to understand its  environment, I used a new virtual machine and recorded the tools that need to be installed. It has been written as a script `setup.sh`.  
## Python2 and Python3  
In python3, in python3 `b'genpart_gen'` and `'genpart_gen'` are different, so they need additional encoding to work properly `.encode('utf-8')`.  
For input 8,16,17,18, they all need this modification.  
```python  
all_particles = pd.DataFrame({name.replace('genpart_',''):df.loc[event_id,name.encode('utf-8')] for name in branches if 'genpart_' in name })  
all_hits = pd.DataFrame({name.replace('rechit_',''):df.loc[event_id,name.encode('utf-8')] for name in branches if 'rechit_' in name })  
cl2d_ind = df.loc[event_id,b"rechit_cluster2d"]  
mcl_ind = df.loc[event_id,b'cluster2d_multicluster'][cl2d_ind]  
```  