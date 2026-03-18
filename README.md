# my-portfolio
// components/WorkGrid.js
import React from 'react';

export default function WorkGrid({ projects }) {
  return (
    <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-10 p-10">
      {projects.map((project) => (
        <div key={project.id} className="group relative cursor-pointer overflow-hidden">
          {/* 静态剧照层 */}
          <img 
            src={project.coverImage} 
            className="w-full aspect-[2.35/1] object-cover transition-opacity duration-500 group-hover:opacity-0"
            alt={project.title}
          />
          
          {/* 悬停视频层：Lux 的精髓 */}
          <video 
            src={project.coverVideo} 
            muted 
            loop 
            playsInline
            onMouseOver={(e) => e.target.play()}
            onMouseOut={(e) => e.target.pause()}
            className="absolute inset-0 w-full h-full object-cover opacity-0 group-hover:opacity-100 transition-opacity duration-500"
          />
          
          {/* 文字信息层 */}
          <div className="mt-4">
            <h3 className="text-[12px] tracking-[0.15em] uppercase font-medium">{project.title}</h3>
            <p className="text-[10px] text-gray-500 tracking-[0.1em] uppercase mt-1">{project.category}</p>
          </div>
        </div>
      ))}
    </div>
  );
}