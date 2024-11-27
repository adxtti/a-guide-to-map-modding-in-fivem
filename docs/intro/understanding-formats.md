
# Understanding GTA V file formats

Grand Theft Auto V uses a diverse range of file formats that define the game world, assets, and behaviors. Understanding these formats is critical for effective map modding and ensures your custom content integrates seamlessly into FiveM.

CodeWalker is a comprehensive tool that accurately parses and allows editing of these file formats. I strongly recommend using CodeWalker’s RPF Explorer as your primary tool for exploring and modifying GTA V’s file structure.

---

## Key file formats in GTA V

### **YMAP (Map Data)**

YMAP files define the placement and properties of objects within the game. This format serves as a blueprint for map design.

```mermaid
flowchart TD
    A[CMapData] -->|Contains| B[CEntityDef]
    A -->|Includes| C[Extension]
    B -->|Has Attribute| D[archetypeName, flags, guid]
    B -->|Has Positioning| E[Position, Rotation, Scale]
    B -->|Contains| F[LOD Data]
    B -->|Uses Extensions| G[Extension]
    G -->|Subtype| H[CExtensionDefLightEffect]
    H -->|Light Properties| I[Primary Color, Intensity, Range]
    I --> J[Additional Lighting Data]
    H -->|Shadow Properties| K[Blur, Near Clip, Far Clip, Intensity]
```

---

### **YTYP (Object Definitions)**

YTYP files define object archetypes, which include the reusable properties for map assets.

```mermaid
flowchart TD
    A[YTYP] -->|Contains| B[Archetypes]
    B -->|Attributes| C[Name, TextureDictionary]
    B -->|Defines| D[Bounds]
    D --> E[Dimensions, Center]
    B -->|LOD Details| F[LOD Distance]
```

---

### **YTD (Texture Dictionary)**

YTD files are repositories of textures, used to apply visual details to models in `.ydr` or `.yft` files.

```mermaid
flowchart TD
    A[YTD] -->|Contains| B[Texture List]
    B -->|Attributes| C[Name, Texture Files]
    B -->|File Types| D[PNG, DDS]
    A -->|Used By| E[YDR, YFT]
```

---

### **YDR (Drawable Models)**

YDR files are used for static or dynamic 3D objects.

```mermaid
flowchart TD
    A[YDR] -->|Defines| B[Mesh Data]
    B -->|Includes| C[Vertices, Faces, Normals]
    A -->|Includes| D[Materials]
    D -->|Attributes| E[Texture Dictionary, Shaders]
    A -->|Optimized By| F[LOD Data]
```

---

### **YFT (Fragment Models)**

YFT files define interactive or dynamic objects, such as vehicles or doors.

```mermaid
flowchart TD
    A[YFT] -->|Includes| B[Mesh Data]
    B -->|Contains| C[Collision Data]
    C -->|Attributes| D[Bounds, Physics]
    A -->|Interactive Objects| E[Vehicles, Doors]
    E -->|Attributes| F[Animations, Movement]
```

---

### **YBN (Collision Bounds)**

YBN files define collision boundaries for various objects, ensuring appropriate physical interactions.

```mermaid
flowchart TD
    A[YBN] -->|Defines| B[Collision Mesh]
    B -->|Composed of| C[Vertices, Edges, Faces]
    B -->|Assigned| D[Materials]
    D -->|Specify| E[Friction, Elasticity, Impact Sound]
    B -->|Approximated by| F[Bounding Volumes]
    F -->|Types| G[Box, Sphere, Capsule]
    A -->|Organized by| H[Hierarchy]
    H -->|Contains| I[Collision Components]
    A -->|Associated with| J[YDR, YFT]
```

---

### **YNV (Navigation Mesh)**

YNV files provide navigation meshes for AI movement.

```mermaid
flowchart TD
    A[YNV] -->|Defines| B[Navigation Areas]
    B -->|Attributes| C[Position, Dimensions]
    B -->|Connected To| D[Links]
    D -->|Defines Movement| E[Vehicles, Pedestrians]
    A -->|Used By AI| F[Pathfinding]
```

---

### **YCD (Clips Dictionary)**

YCD files store animation data for characters and objects.

```mermaid
flowchart TD
    A[YCD] -->|Stores| B[Animation Clips]
    B -->|Attributes| C[Duration, Transitions]
    B -->|References| D[Skeletal Models]
    A -->|Used By| E[Characters, Vehicles]
```

---

## Review of file formats

1. **YMAP**: Place entities and props in the world
2. **YTYP**: Define reusable object archetypes
3. **YDR/YFT**: Provide models and interactive objects
4. **YTD**: Supply textures for visual representation
5. **YBN**: Define collision boundaries for physical interactions
6. **YNV**: Set up navigation for AI pathfinding
7. **YCD**: Define animations for characters and objects

---

This reference consolidates the core GTA V file formats and their interrelations for modding and custom map modding.