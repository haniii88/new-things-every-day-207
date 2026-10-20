```javascript
function dailyLog207() {
  const services = [
    { name: "API Server", uptime: 99.95, status: "online" },
    { name: "Database", uptime: 98.40, status: "online" },
    { name: "Authentication", uptime: 96.20, status: "degraded" },
    { name: "File Storage", uptime: 99.80, status: "online" },
    { name: "Email Service", uptime: 92.50, status: "offline" },
  ];

  const averageUptime =
    services.reduce((sum, service) => sum + service.uptime, 0) /
    services.length;

  const issues = services.filter(
    service => service.status !== "online"
  );

  console.log("=== Server Health Report ===");
  console.log(`Total Services: ${services.length}`);
  console.log(`Average Uptime: ${averageUptime.toFixed(2)}%`);
  console.log(`Services Needing Attention: ${issues.length}`);

  services.forEach(service => {
    const icon =
      service.status === "online" ? "✅" :
      service.status === "degraded" ? "⚠️" : "❌";

    console.log(
      `${icon} ${service.name}: ${service.uptime}% uptime`
    );
  });

  console.log(
    averageUptime >= 99
      ? "\nSystem availability is healthy."
      : "\nReview service reliability and investigate incidents."
  );
}

dailyLog207();
```
