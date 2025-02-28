:github_url: hide

.. DO NOT EDIT THIS FILE!!!
.. Generated automatically from Godot engine sources.
.. Generator: https://github.com/godotengine/godot/tree/master/doc/tools/make_rst.py.
.. XML source: https://github.com/godotengine/godot/tree/master/doc/classes/ReflectionProbe.xml.

.. _class_ReflectionProbe:

ReflectionProbe
===============

**Inherits:** :ref:`VisualInstance3D<class_VisualInstance3D>` **<** :ref:`Node3D<class_Node3D>` **<** :ref:`Node<class_Node>` **<** :ref:`Object<class_Object>`

Captures its surroundings to create fast, accurate reflections from a given point.

.. rst-class:: classref-introduction-group

Description
-----------

Captures its surroundings as a cubemap, and stores versions of it with increasing levels of blur to simulate different material roughnesses.

The **ReflectionProbe** is used to create high-quality reflections at a low performance cost (when :ref:`update_mode<class_ReflectionProbe_property_update_mode>` is :ref:`UPDATE_ONCE<class_ReflectionProbe_constant_UPDATE_ONCE>`). **ReflectionProbe**\ s can be blended together and with the rest of the scene smoothly. **ReflectionProbe**\ s can also be combined with :ref:`VoxelGI<class_VoxelGI>`, SDFGI (:ref:`Environment.sdfgi_enabled<class_Environment_property_sdfgi_enabled>`) and screen-space reflections (:ref:`Environment.ssr_enabled<class_Environment_property_ssr_enabled>`) to get more accurate reflections in specific areas. **ReflectionProbe**\ s render all objects within their :ref:`cull_mask<class_ReflectionProbe_property_cull_mask>`, so updating them can be quite expensive. It is best to update them once with the important static objects and then leave them as-is.

\ **Note:** Unlike :ref:`VoxelGI<class_VoxelGI>` and SDFGI, **ReflectionProbe**\ s only source their environment from a :ref:`WorldEnvironment<class_WorldEnvironment>` node. If you specify an :ref:`Environment<class_Environment>` resource within a :ref:`Camera3D<class_Camera3D>` node, it will be ignored by the **ReflectionProbe**. This can lead to incorrect lighting within the **ReflectionProbe**.

.. rst-class:: classref-introduction-group

Tutorials
---------

- :doc:`Reflection probes <../tutorials/3d/reflection_probes>`

.. rst-class:: classref-reftable-group

Properties
----------

.. table::
   :widths: auto

   +------------------------------------------------------+----------------------------------------------------------------------------------+-------------------------+
   | :ref:`Color<class_Color>`                            | :ref:`ambient_color<class_ReflectionProbe_property_ambient_color>`               | ``Color(0, 0, 0, 1)``   |
   +------------------------------------------------------+----------------------------------------------------------------------------------+-------------------------+
   | :ref:`float<class_float>`                            | :ref:`ambient_color_energy<class_ReflectionProbe_property_ambient_color_energy>` | ``1.0``                 |
   +------------------------------------------------------+----------------------------------------------------------------------------------+-------------------------+
   | :ref:`AmbientMode<enum_ReflectionProbe_AmbientMode>` | :ref:`ambient_mode<class_ReflectionProbe_property_ambient_mode>`                 | ``1``                   |
   +------------------------------------------------------+----------------------------------------------------------------------------------+-------------------------+
   | :ref:`bool<class_bool>`                              | :ref:`box_projection<class_ReflectionProbe_property_box_projection>`             | ``false``               |
   +------------------------------------------------------+----------------------------------------------------------------------------------+-------------------------+
   | :ref:`int<class_int>`                                | :ref:`cull_mask<class_ReflectionProbe_property_cull_mask>`                       | ``1048575``             |
   +------------------------------------------------------+----------------------------------------------------------------------------------+-------------------------+
   | :ref:`bool<class_bool>`                              | :ref:`enable_shadows<class_ReflectionProbe_property_enable_shadows>`             | ``false``               |
   +------------------------------------------------------+----------------------------------------------------------------------------------+-------------------------+
   | :ref:`Vector3<class_Vector3>`                        | :ref:`extents<class_ReflectionProbe_property_extents>`                           | ``Vector3(10, 10, 10)`` |
   +------------------------------------------------------+----------------------------------------------------------------------------------+-------------------------+
   | :ref:`float<class_float>`                            | :ref:`intensity<class_ReflectionProbe_property_intensity>`                       | ``1.0``                 |
   +------------------------------------------------------+----------------------------------------------------------------------------------+-------------------------+
   | :ref:`bool<class_bool>`                              | :ref:`interior<class_ReflectionProbe_property_interior>`                         | ``false``               |
   +------------------------------------------------------+----------------------------------------------------------------------------------+-------------------------+
   | :ref:`float<class_float>`                            | :ref:`max_distance<class_ReflectionProbe_property_max_distance>`                 | ``0.0``                 |
   +------------------------------------------------------+----------------------------------------------------------------------------------+-------------------------+
   | :ref:`float<class_float>`                            | :ref:`mesh_lod_threshold<class_ReflectionProbe_property_mesh_lod_threshold>`     | ``1.0``                 |
   +------------------------------------------------------+----------------------------------------------------------------------------------+-------------------------+
   | :ref:`Vector3<class_Vector3>`                        | :ref:`origin_offset<class_ReflectionProbe_property_origin_offset>`               | ``Vector3(0, 0, 0)``    |
   +------------------------------------------------------+----------------------------------------------------------------------------------+-------------------------+
   | :ref:`UpdateMode<enum_ReflectionProbe_UpdateMode>`   | :ref:`update_mode<class_ReflectionProbe_property_update_mode>`                   | ``0``                   |
   +------------------------------------------------------+----------------------------------------------------------------------------------+-------------------------+

.. rst-class:: classref-section-separator

----

.. rst-class:: classref-descriptions-group

Enumerations
------------

.. _enum_ReflectionProbe_UpdateMode:

.. rst-class:: classref-enumeration

enum **UpdateMode**:

.. _class_ReflectionProbe_constant_UPDATE_ONCE:

.. rst-class:: classref-enumeration-constant

:ref:`UpdateMode<enum_ReflectionProbe_UpdateMode>` **UPDATE_ONCE** = ``0``

Update the probe once on the next frame (recommended for most objects). The corresponding radiance map will be generated over the following six frames. This takes more time to update than :ref:`UPDATE_ALWAYS<class_ReflectionProbe_constant_UPDATE_ALWAYS>`, but it has a lower performance cost and can result in higher-quality reflections. The ReflectionProbe is updated when its transform changes, but not when nearby geometry changes. You can force a **ReflectionProbe** update by moving the **ReflectionProbe** slightly in any direction.

.. _class_ReflectionProbe_constant_UPDATE_ALWAYS:

.. rst-class:: classref-enumeration-constant

:ref:`UpdateMode<enum_ReflectionProbe_UpdateMode>` **UPDATE_ALWAYS** = ``1``

Update the probe every frame. This provides better results for fast-moving dynamic objects (such as cars). However, it has a significant performance cost. Due to the cost, it's recommended to only use one ReflectionProbe with :ref:`UPDATE_ALWAYS<class_ReflectionProbe_constant_UPDATE_ALWAYS>` at most per scene. For all other use cases, use :ref:`UPDATE_ONCE<class_ReflectionProbe_constant_UPDATE_ONCE>`.

.. rst-class:: classref-item-separator

----

.. _enum_ReflectionProbe_AmbientMode:

.. rst-class:: classref-enumeration

enum **AmbientMode**:

.. _class_ReflectionProbe_constant_AMBIENT_DISABLED:

.. rst-class:: classref-enumeration-constant

:ref:`AmbientMode<enum_ReflectionProbe_AmbientMode>` **AMBIENT_DISABLED** = ``0``

Do not apply any ambient lighting inside the **ReflectionProbe**'s :ref:`extents<class_ReflectionProbe_property_extents>`.

.. _class_ReflectionProbe_constant_AMBIENT_ENVIRONMENT:

.. rst-class:: classref-enumeration-constant

:ref:`AmbientMode<enum_ReflectionProbe_AmbientMode>` **AMBIENT_ENVIRONMENT** = ``1``

Apply automatically-sourced environment lighting inside the **ReflectionProbe**'s :ref:`extents<class_ReflectionProbe_property_extents>`.

.. _class_ReflectionProbe_constant_AMBIENT_COLOR:

.. rst-class:: classref-enumeration-constant

:ref:`AmbientMode<enum_ReflectionProbe_AmbientMode>` **AMBIENT_COLOR** = ``2``

Apply custom ambient lighting inside the **ReflectionProbe**'s :ref:`extents<class_ReflectionProbe_property_extents>`. See :ref:`ambient_color<class_ReflectionProbe_property_ambient_color>` and :ref:`ambient_color_energy<class_ReflectionProbe_property_ambient_color_energy>`.

.. rst-class:: classref-section-separator

----

.. rst-class:: classref-descriptions-group

Property Descriptions
---------------------

.. _class_ReflectionProbe_property_ambient_color:

.. rst-class:: classref-property

:ref:`Color<class_Color>` **ambient_color** = ``Color(0, 0, 0, 1)``

.. rst-class:: classref-property-setget

- void **set_ambient_color** **(** :ref:`Color<class_Color>` value **)**
- :ref:`Color<class_Color>` **get_ambient_color** **(** **)**

The custom ambient color to use within the **ReflectionProbe**'s :ref:`extents<class_ReflectionProbe_property_extents>`. Only effective if :ref:`ambient_mode<class_ReflectionProbe_property_ambient_mode>` is :ref:`AMBIENT_COLOR<class_ReflectionProbe_constant_AMBIENT_COLOR>`.

.. rst-class:: classref-item-separator

----

.. _class_ReflectionProbe_property_ambient_color_energy:

.. rst-class:: classref-property

:ref:`float<class_float>` **ambient_color_energy** = ``1.0``

.. rst-class:: classref-property-setget

- void **set_ambient_color_energy** **(** :ref:`float<class_float>` value **)**
- :ref:`float<class_float>` **get_ambient_color_energy** **(** **)**

The custom ambient color energy to use within the **ReflectionProbe**'s :ref:`extents<class_ReflectionProbe_property_extents>`. Only effective if :ref:`ambient_mode<class_ReflectionProbe_property_ambient_mode>` is :ref:`AMBIENT_COLOR<class_ReflectionProbe_constant_AMBIENT_COLOR>`.

.. rst-class:: classref-item-separator

----

.. _class_ReflectionProbe_property_ambient_mode:

.. rst-class:: classref-property

:ref:`AmbientMode<enum_ReflectionProbe_AmbientMode>` **ambient_mode** = ``1``

.. rst-class:: classref-property-setget

- void **set_ambient_mode** **(** :ref:`AmbientMode<enum_ReflectionProbe_AmbientMode>` value **)**
- :ref:`AmbientMode<enum_ReflectionProbe_AmbientMode>` **get_ambient_mode** **(** **)**

The ambient color to use within the **ReflectionProbe**'s :ref:`extents<class_ReflectionProbe_property_extents>`. The ambient color will smoothly blend with other **ReflectionProbe**\ s and the rest of the scene (outside the **ReflectionProbe**'s :ref:`extents<class_ReflectionProbe_property_extents>`).

.. rst-class:: classref-item-separator

----

.. _class_ReflectionProbe_property_box_projection:

.. rst-class:: classref-property

:ref:`bool<class_bool>` **box_projection** = ``false``

.. rst-class:: classref-property-setget

- void **set_enable_box_projection** **(** :ref:`bool<class_bool>` value **)**
- :ref:`bool<class_bool>` **is_box_projection_enabled** **(** **)**

If ``true``, enables box projection. This makes reflections look more correct in rectangle-shaped rooms by offsetting the reflection center depending on the camera's location.

\ **Note:** To better fit rectangle-shaped rooms that are not aligned to the grid, you can rotate the **ReflectionProbe** node.

.. rst-class:: classref-item-separator

----

.. _class_ReflectionProbe_property_cull_mask:

.. rst-class:: classref-property

:ref:`int<class_int>` **cull_mask** = ``1048575``

.. rst-class:: classref-property-setget

- void **set_cull_mask** **(** :ref:`int<class_int>` value **)**
- :ref:`int<class_int>` **get_cull_mask** **(** **)**

Sets the cull mask which determines what objects are drawn by this probe. Every :ref:`VisualInstance3D<class_VisualInstance3D>` with a layer included in this cull mask will be rendered by the probe. To improve performance, it is best to only include large objects which are likely to take up a lot of space in the reflection.

.. rst-class:: classref-item-separator

----

.. _class_ReflectionProbe_property_enable_shadows:

.. rst-class:: classref-property

:ref:`bool<class_bool>` **enable_shadows** = ``false``

.. rst-class:: classref-property-setget

- void **set_enable_shadows** **(** :ref:`bool<class_bool>` value **)**
- :ref:`bool<class_bool>` **are_shadows_enabled** **(** **)**

If ``true``, computes shadows in the reflection probe. This makes the reflection probe slower to render; you may want to disable this if using the :ref:`UPDATE_ALWAYS<class_ReflectionProbe_constant_UPDATE_ALWAYS>` :ref:`update_mode<class_ReflectionProbe_property_update_mode>`.

.. rst-class:: classref-item-separator

----

.. _class_ReflectionProbe_property_extents:

.. rst-class:: classref-property

:ref:`Vector3<class_Vector3>` **extents** = ``Vector3(10, 10, 10)``

.. rst-class:: classref-property-setget

- void **set_extents** **(** :ref:`Vector3<class_Vector3>` value **)**
- :ref:`Vector3<class_Vector3>` **get_extents** **(** **)**

The size of the reflection probe. The larger the extents, the more space covered by the probe, which will lower the perceived resolution. It is best to keep the extents only as large as you need them.

\ **Note:** To better fit areas that are not aligned to the grid, you can rotate the **ReflectionProbe** node.

.. rst-class:: classref-item-separator

----

.. _class_ReflectionProbe_property_intensity:

.. rst-class:: classref-property

:ref:`float<class_float>` **intensity** = ``1.0``

.. rst-class:: classref-property-setget

- void **set_intensity** **(** :ref:`float<class_float>` value **)**
- :ref:`float<class_float>` **get_intensity** **(** **)**

Defines the reflection intensity. Intensity modulates the strength of the reflection.

.. rst-class:: classref-item-separator

----

.. _class_ReflectionProbe_property_interior:

.. rst-class:: classref-property

:ref:`bool<class_bool>` **interior** = ``false``

.. rst-class:: classref-property-setget

- void **set_as_interior** **(** :ref:`bool<class_bool>` value **)**
- :ref:`bool<class_bool>` **is_set_as_interior** **(** **)**

If ``true``, reflections will ignore sky contribution.

.. rst-class:: classref-item-separator

----

.. _class_ReflectionProbe_property_max_distance:

.. rst-class:: classref-property

:ref:`float<class_float>` **max_distance** = ``0.0``

.. rst-class:: classref-property-setget

- void **set_max_distance** **(** :ref:`float<class_float>` value **)**
- :ref:`float<class_float>` **get_max_distance** **(** **)**

The maximum distance away from the **ReflectionProbe** an object can be before it is culled. Decrease this to improve performance, especially when using the :ref:`UPDATE_ALWAYS<class_ReflectionProbe_constant_UPDATE_ALWAYS>` :ref:`update_mode<class_ReflectionProbe_property_update_mode>`.

\ **Note:** The maximum reflection distance is always at least equal to the :ref:`extents<class_ReflectionProbe_property_extents>`. This means that decreasing :ref:`max_distance<class_ReflectionProbe_property_max_distance>` will not always cull objects from reflections, especially if the reflection probe's :ref:`extents<class_ReflectionProbe_property_extents>` are already large.

.. rst-class:: classref-item-separator

----

.. _class_ReflectionProbe_property_mesh_lod_threshold:

.. rst-class:: classref-property

:ref:`float<class_float>` **mesh_lod_threshold** = ``1.0``

.. rst-class:: classref-property-setget

- void **set_mesh_lod_threshold** **(** :ref:`float<class_float>` value **)**
- :ref:`float<class_float>` **get_mesh_lod_threshold** **(** **)**

The automatic LOD bias to use for meshes rendered within the **ReflectionProbe** (this is analog to :ref:`Viewport.mesh_lod_threshold<class_Viewport_property_mesh_lod_threshold>`). Higher values will use less detailed versions of meshes that have LOD variations generated. If set to ``0.0``, automatic LOD is disabled. Increase :ref:`mesh_lod_threshold<class_ReflectionProbe_property_mesh_lod_threshold>` to improve performance at the cost of geometry detail, especially when using the :ref:`UPDATE_ALWAYS<class_ReflectionProbe_constant_UPDATE_ALWAYS>` :ref:`update_mode<class_ReflectionProbe_property_update_mode>`.

\ **Note:** :ref:`mesh_lod_threshold<class_ReflectionProbe_property_mesh_lod_threshold>` does not affect :ref:`GeometryInstance3D<class_GeometryInstance3D>` visibility ranges (also known as "manual" LOD or hierarchical LOD).

.. rst-class:: classref-item-separator

----

.. _class_ReflectionProbe_property_origin_offset:

.. rst-class:: classref-property

:ref:`Vector3<class_Vector3>` **origin_offset** = ``Vector3(0, 0, 0)``

.. rst-class:: classref-property-setget

- void **set_origin_offset** **(** :ref:`Vector3<class_Vector3>` value **)**
- :ref:`Vector3<class_Vector3>` **get_origin_offset** **(** **)**

Sets the origin offset to be used when this **ReflectionProbe** is in :ref:`box_projection<class_ReflectionProbe_property_box_projection>` mode. This can be set to a non-zero value to ensure a reflection fits a rectangle-shaped room, while reducing the number of objects that "get in the way" of the reflection.

.. rst-class:: classref-item-separator

----

.. _class_ReflectionProbe_property_update_mode:

.. rst-class:: classref-property

:ref:`UpdateMode<enum_ReflectionProbe_UpdateMode>` **update_mode** = ``0``

.. rst-class:: classref-property-setget

- void **set_update_mode** **(** :ref:`UpdateMode<enum_ReflectionProbe_UpdateMode>` value **)**
- :ref:`UpdateMode<enum_ReflectionProbe_UpdateMode>` **get_update_mode** **(** **)**

Sets how frequently the **ReflectionProbe** is updated. Can be :ref:`UPDATE_ONCE<class_ReflectionProbe_constant_UPDATE_ONCE>` or :ref:`UPDATE_ALWAYS<class_ReflectionProbe_constant_UPDATE_ALWAYS>`.

.. |virtual| replace:: :abbr:`virtual (This method should typically be overridden by the user to have any effect.)`
.. |const| replace:: :abbr:`const (This method has no side effects. It doesn't modify any of the instance's member variables.)`
.. |vararg| replace:: :abbr:`vararg (This method accepts any number of arguments after the ones described here.)`
.. |constructor| replace:: :abbr:`constructor (This method is used to construct a type.)`
.. |static| replace:: :abbr:`static (This method doesn't need an instance to be called, so it can be called directly using the class name.)`
.. |operator| replace:: :abbr:`operator (This method describes a valid operator to use with this type as left-hand operand.)`
