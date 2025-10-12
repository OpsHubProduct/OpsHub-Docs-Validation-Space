## Description

Team Foundation Server (TFS)/Azure DevOps provides the functionality to add an image in discussion/comment. How that functionality works after synchronization by <code class="expression">space.vars.SITENAME</code>.

## Solution

You can add an image in discussion/comment from the systems’ User Interface. But right now <code class="expression">space.vars.SITENAME</code> does not provide this feature. Once the discussion/comment is synchronized to the target system, it will put the source inline-image URL as it is in the target system's field/comment/discussion without transformation. So target end system comment image will still be pointing to the source endpoint. The image will be shown in the target endpoint's comment if the target endpoint is connected to the source endpoint, but once the source endpoint is disconnected from the target it will not be shown.
