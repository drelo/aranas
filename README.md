# aranas
codigo cp

```bash
# extract the desired columns or text
awk '{print $1 $NF}' MODEL  > MODEL2   
# replace multiple strings inplace
sed -i 's~./FASTA/~~g; s~.fas~~g; s~.iqtree:Best-fit~ ~g; s~$~,~g' MODEL2
# switch order of columns or text
awk '{print $2" "$1}' MODEL2 > MODEL3
# exract only 2 columns from the partition file generated with AMAS
# At this stage we can compare both 'MODEL3' and 'partition.part' columns to confirm the order of the loci listed in both files
awk '{print $2" "$NF}' partition.part > LENGTH
# This will paste both files to obtain the "partitionmodels" file
paste MODEL3 LENGTH > partitionmodels
```

Finally I run IQTREE with this line

```
