#!/usr/bin/env bash
# Complete system update and cleanup script

# Exit immediately if a command exits with a non-zero status
set -e

echo "📦 Updating package list..."
sudo nala update

echo "⬆️ Performing full system upgrade..."
sudo nala full-upgrade -y

echo "🧹 Removing unnecessary packages..."
sudo nala autoremove -y

echo "🧼 Cleaning downloaded package cache..."
sudo nala clean
echo "✅ Done with Apt"

echo "Phase 2: 📦 Updating Flatpak packages..."
sudo flatpak update -y

echo "🧽 Cleaning system Flatpaks..."
sudo flatpak uninstall --unused -y
sudo flatpak repair

echo "✅ Done with flatpaks"

echo "✅ Your system is fully updated and cleaned up!"
