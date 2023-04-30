# WebGL - Pipeline, Varyings and Fragments

In WebGL, the flow of pixel data can be understood as a pipeline consisting of several stages. Here's an overview of the main stages in the WebGL rendering pipeline:

- Vertex data input: The first step in the pipeline is to provide the vertex data for the objects you want to render. Vertex data usually includes positions, colors, texture coordinates, and other attributes. These attributes are defined as buffers and passed to the vertex shader.

- Vertex shader: The vertex shader is a programmable stage in the pipeline that processes each vertex individually. Its primary responsibility is to transform the input vertex positions from object space to clip space. It can also perform other operations, such as calculating per-vertex lighting or transforming other attributes like texture coordinates or normals.

- Primitive assembly: After the vertex shader processes the vertices, they are assembled into primitives like points, lines, or triangles. These primitives are then clipped and transformed into screen space.

- Rasterization: In this stage, the primitives are converted into fragments (pixels) that will be processed by the fragment shader. Rasterization includes interpolation of vertex attributes like colors and texture coordinates across the primitive.

- Fragment shader: The fragment shader is another programmable stage in the pipeline that processes each fragment (pixel) individually. Its primary responsibility is to compute the final color of the fragment, which can involve tasks like texture sampling, per-pixel lighting, or other custom operations.

- Depth and stencil testing: Before the final color of the fragment is written to the framebuffer, depth and stencil tests are performed to determine if the fragment should be discarded or not. This helps in resolving visibility and handling effects like masking.

- Blending: If the fragment passes the depth and stencil tests, it is blended with the existing color in the framebuffer according to the specified blending function. This step allows for transparency and other effects.

- Framebuffer output: The final color of the fragment is written to the framebuffer, which can be the default framebuffer that represents the screen, or a custom framebuffer used for offscreen rendering or post-processing.

This overview simplifies the actual pipeline, but it should give you a general understanding of the flow of pixel data in WebGL. Note that this pipeline is designed for real-time rendering and may not be applicable for offline or non-real-time rendering techniques.

To clarify, the vertex shader processes all vertices first, and then the pipeline moves on to the fragment shader stage. The vertex and fragment shaders don't work sequentially on individual vertices.

    > Q) If so, then how varyings for different vertices are passed on to fragment shader

When a varying variable is used in a vertex shader, its value is interpolated across the primitive (e.g., triangle) during the rasterization stage. This interpolation generates per-fragment values for the varying variable, which are then passed to the fragment shader.

Let me illustrate this with an example:

In the vertex shader, you declare a varying variable, say, varying vec3 vColor; and set its value based on the vertex attributes, such as color or position.

When the vertex shader processes all vertices and the primitive assembly stage assembles the vertices into primitives, the varying variables have specific values for each vertex.

During the rasterization stage, WebGL interpolates the varying variables' values across the primitive, generating a value for each fragment. This interpolation is typically done using barycentric coordinates or other interpolation methods, depending on the GPU hardware.

For each fragment, the interpolated value of the varying variable is then passed to the fragment shader. In the fragment shader, you can use the varying variable value to compute the final color of the fragment or perform other operations.

So, while the vertex and fragment shaders don't work sequentially on individual vertices, the varying variables are interpolated during rasterization, allowing per-fragment values to be passed to the fragment shader.
