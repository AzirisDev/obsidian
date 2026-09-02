Copy files from build context into the image.

```
# Copy single file
COPY start /app/

# Copy directory contents
COPY scripts/ /app/scripts/

# Copy multiple files
COPY config.json data.json /app/

# Copy with different name
COPY config.prod.json /app/config.json
```


Links:

202609021455

